---
title: "Rubygems installation problem"
date: 2008-09-11
forum: General Help
---

### Post by mamboze on 2008-09-11
I've got a problem installing RubyGems on Hardy. I installed RubyGems with Synaptic. Then reading RubyGems User Guide to familiarize, I ran a few gem commands, these worked. Then I ran
gem update --system  

This seems to have broken gems. 
If I now run
gem query --remote

I get this message:
/usr/bin/gem:23: uninitialized constant Gem::GemRunner (NameError)

and 
gem_server 
gives this:
/usr/bin/gem:23: uninitialized constant Gem::GemRunner (NameError)
with gem_server
/usr/local/lib/site_ruby/1.8/rubygems/server.rb:331:in `[]': Symbol as array index (TypeError)
	from /usr/local/lib/site_ruby/1.8/rubygems/server.rb:331:in `run'
	from /usr/bin/gem_server:5

I've uninstalled and reinstalled Rubygems thru synaptic, trying to undo the gem upgrade but no fix. 

Any help would be greatly appreciated

---

