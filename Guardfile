# A sample Guardfile
# More info at https://github.com/guard/guard#readme

guard 'bundler' do
  watch('Gemfile')
  watch(/^.+\.gemspec/)
end

rspec_options = {
  all_after_pass: false,
  all_on_start: false,
  failed_mode: :keep,
  cmd: 'bundle exec rspec',
}

guard 'rspec', rspec_options do
  watch(%r{^spec/.+_spec\.rb$})
  watch(%r{^lib/(.+)\.rb$}) { |m| "spec/#{m[1]}_spec.rb" }
  watch(%r{^lib/flipper/api/v1/actions/events.rb$}) { |_m| "spec/flipper/cloud_spec.rb" }
  watch(%r{^lib/flipper/cloud.*}) { |_m| "spec/flipper/cloud_spec.rb" }
  watch(/shared_adapter_specs\.rb$/) { 'spec' }
  watch('spec/helper.rb') { 'spec' }
end

coffee_options = {
  input: 'lib/flipper/ui/assets/javascripts',
  output: 'lib/flipper/ui/public/js',
  all_on_start: false,
}
guard 'coffeescript', coffee_options

sass_options = {
  input: 'lib/flipper/ui/assets/stylesheets',
  output: 'lib/flipper/ui/public/css',
}
guard 'sass', sass_options

guard :rubocop do
  watch(/.+\.rb$/)
  watch(%r{(?:.+/)?\.rubocop(?:_todo)?\.yml$}) { |m| File.dirname(m[0]) }
end
