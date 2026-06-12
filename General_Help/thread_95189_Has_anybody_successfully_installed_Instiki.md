---
title: "Has anybody successfully installed Instiki?"
date: 2005-11-25
forum: General Help
---

### Post by ryharv on 2005-11-25
trying to install instiki.  already installed ruby and instiki, but cannot run instiki.  the directions on instiki.org indicate to run "ruby instiki."  then i get all this:

ryan@webb-temp:~/public_html $ ruby /usr/bin/instiki
/usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:68:in `dup': allocator undefined for Proc (NoMethodError)
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:68:in `dup'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:66:in `each'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:66:in `dup'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:46:in `method_missing'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:46:in `indent'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/code_generation.rb:46:in `method_missing'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/routing.rb:451:in `write_recognition'
        from /usr/lib/ruby/gems/1.8/gems/actionpack-1.9.1/lib/action_controller/routing.rb:553:in `draw'
         ... 11 levels...
        from /usr/lib/ruby/gems/1.8/gems/instiki-0.10.2/./instiki:6
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.1.1/lib/active_support/dependencies.rb:193:in `load'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.1.1/lib/active_support/dependencies.rb:193:in `load'
        from /usr/bin/instiki:18

Has anybody successfully gotten around this?

---

