$:.unshift File.expand_path('..', __FILE__)
require 'rake/testtask'
CORE = %w(state_machines)
INTEGRATIONS = %w(state_machines-activemodel state_machines-activerecord)
PROJECTS = CORE + INTEGRATIONS

INTEGRATIONS.each do |task_name|
  desc "Run test for #{task_name}"
  task "test:#{task_name}" do
    system(%(cd #{task_name} && appraisal rake))
  end
  desc "Appraisal install for #{task_name}"
  task "appraisal:#{task_name}" do
    system(%(cd #{task_name} && appraisal install))
  end
end

desc "Run test for state_machines"
task "test:state_machines" do
  system(%(cd state_machines && rake))
end

desc 'Test core and all integration'
task 'test:all' => %w(test:state_machines state_machines-activemodel test:state_machines-activerecord)