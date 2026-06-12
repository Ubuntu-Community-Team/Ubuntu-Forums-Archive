---
title: "rake error"
date: 2008-10-16
forum: General Help
---

### Post by haize on 2008-10-16
I installed rails 2.1.1 and ruby 1.8.6.
when I run: rake db:migrate
I get an error:
/usr/bin/rake:27:in `require': no such file to load -- rake (LoadError)

what should I do?

---

### Post by dwain12 on 2009-03-07
i am new to ruby on rails and i am trying to rake my brogram but all it does is:

rake aborted!
Test failures

(See full trace by running task with --trace)
dwain@personal:~/project/stuad$ rake --trace
(in /home/dwain/project/stuad)
/home/dwain/project/stuad/config/boot.rb:29:Warning: require_gem is obsolete.  Use gem instead.
** Invoke default (first_time)
** Invoke test (first_time)
** Execute test
** Invoke test:units (first_time)
** Invoke db:test:prepare (first_time)
** Invoke environment (first_time)
** Execute environment
** Execute db:test:prepare
** Invoke db:test:clone (first_time)
** Invoke db:schema:dump (first_time)
** Invoke environment 
** Execute db:schema:dump
** Invoke db:test:purge (first_time)
** Invoke environment 
** Execute db:test:purge
** Execute db:test:clone
** Invoke db:schema:load (first_time)
** Invoke environment 
** Execute db:schema:load
** Execute test:units
** Invoke test:functionals (first_time)
** Invoke db:test:prepare 
** Execute test:functionals
** Invoke test:integration (first_time)
** Invoke db:test:prepare 
** Execute test:integration
rake aborted!
Test failures
/usr/local/lib/ruby/gems/1.8/gems/rails-1.2.1/lib/tasks/testing.rake:50
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:387:in `call'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:387:in `execute'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:387:in `each'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:387:in `execute'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:357:in `invoke'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:350:in `synchronize'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:350:in `invoke'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:364:in `invoke_prerequisites'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:999:in `each'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:999:in `send'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:999:in `each'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:363:in `invoke_prerequisites'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:356:in `invoke'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:350:in `synchronize'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:350:in `invoke'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:1906:in `run'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:1906:in `each'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/lib/rake.rb:1906:in `run'
/usr/local/lib/ruby/gems/1.8/gems/rake-0.7.1/bin/rake:7
/usr/local/bin/rake:16:in `load'
/usr/local/bin/rake:16


. Can some one tell me what is wrong with it please?

---

### Post by hydro on 2010-04-13
> **haize said:**
> I installed rails 2.1.1 and ruby 1.8.6.
when I run: rake db:migrate
I get an error:
/usr/bin/rake:27:in `require': no such file to load -- rake (LoadError)

what should I do?

For those who get this error:
Check if you installed rake (sudo gem install rake)
Check your symlinks. Maybe rake does not point to /usr/local/bin/rake espacially if you had gem installed by apt.

---

