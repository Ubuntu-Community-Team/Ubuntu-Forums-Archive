---
title: "ruby gems"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by artgressick on 2008-12-23
hello, I am installing ruby gems on Ubuntu 8.10 with ruby 1.8.7 and having problems with installing rubynode I have search for more then 6 hours on the web with no luck. I have tried everything.

I installed the ruby libraries and everything. I am down to the final pieces and could use some help

gem install rubynode

Building native extensions.  This could take a while...
ERROR:  Error installing rubynode:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install rubynode
==================== ERROR =====================
Please set RUBY_SOURCE_DIR to the source path of ruby 1.8.7 (2008-08-11)!
================================================


Gem files will remain installed in /var/lib/gems/1.8/gems/rubynode-0.1.5 for inspection.
Results logged to /var/lib/gems/1.8/gems/rubynode-0.1.5/ext/rubynode_ext/gem_make.out

I tried the:

RUBY_SOURCE_DIR="/usr/bin/ruby1.8" gem install rubynode
RUBY_SOURCE_DIR="/usr/lib/ruby/1.8/i486-linux" gem install rubynode
RUBY_SOURCE_DIR="/usr/lib/ruby/1.8" gem install rubynode

nothing seems to work and I really need some help

---

### Post by ozaki on 2010-05-13
to dear [artgressick]("http://ubuntuforums.org/member.php?u=733194")
    hi, this question is you must give your "RUBY INSTALL SOURCE DIR" to it,
    since it wanna your gc.c file.
    like this: RUBY_SOURCE_DIR="YOUR_RUBY_INSTALL_DIR" gam install bla..bla..bla
    
    wish can help you.
    and my email is [email]ozaki.lsc@gmail.com[/email], from china, a ruby fan. Contact with me. thx!

---

### Post by dino99 on 2010-05-13
> **ozaki said:**
> to dear [artgressick]("http://ubuntuforums.org/member.php?u=733194")
    hi, this question is you must give your "RUBY INSTALL SOURCE DIR" to it,
    since it wanna your gc.c file.
    like this: RUBY_SOURCE_DIR="YOUR_RUBY_INSTALL_DIR" gam install bla..bla..bla
    
    wish can help you.
    and my email is xxxxxx, from china, a ruby fan. Contact with me. thx!

dear fan,
you might erase your mail if you want stay away a bunch of spams and others nice things :confused:

but i hope your answer was not still waited ('2008') :P

---

### Post by ozaki on 2010-05-13
god.... i didnt notice the time...2008...
but there is something reply better than empty. :-):P

---

