---
title: "Trouble installing ruby on rails"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by dogas on 2006-01-13
Hi guys,

I have been banging my head against the wall with trying to install rails. I have tried the packages way and also the manual install, both of which do not work.  For the package method, I have been following the instructions here:

[http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable)

The problem occurs when I try to install rubygems --
[FONT="Courier New"]
root@HOST16:/home/grant/My Downloads/rubygems-0.8.11# ruby setup.rb
setup.rb:52:in `require': No such file to load -- rbconfig (LoadError)
        from setup.rb:52
[/FONT]

It looks like the ruby package is not installing a critical component.  So then I removed the packages and tried to compile and install manually, and I ran directly into [this guy's]("http://ubuntuforums.org/showthread.php?t=104272&highlight=rails+zlib") problem.. although he wasn't kind enough to explain how he fixed it.

At this point I've been going at it for 2 hours, and I'm so fed up with how poor (in my opinion) ubuntu's support for ruby and rails is that I'm about to go back to Gentoo.

Any help would be appreciated!  

-Grant

---

### Post by vijayramanan on 2006-04-22
[QUOTE=dogas]Hi guys,

I have been banging my head against the wall with trying to install rails. I have tried the packages way and also the manual install, both of which do not work.  For the package method, I have been following the instructions here:

[http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable)

The problem occurs when I try to install rubygems --
[FONT="Courier New"]
root@HOST16:/home/grant/My Downloads/rubygems-0.8.11# ruby setup.rb
setup.rb:52:in `require': No such file to load -- rbconfig (LoadError)
        from setup.rb:52
[/FONT]

It looks like the ruby package is not installing a critical component.  So then I removed the packages and tried to compile and install manually, and I ran directly into [this guy's]("http://ubuntuforums.org/showthread.php?t=104272&highlight=rails+zlib") problem.. although he wasn't kind enough to explain how he fixed it.

At this point I've been going at it for 2 hours, and I'm so fed up with how poor (in my opinion) ubuntu's support for ruby and rails is that I'm about to go back to Gentoo.

Any help would be appreciated!  

-Grant[/QUOTE]

hI there
I faced the same problem.. 

I can only tell you what i remember... Coz i tried a dozen things and this finally clicked..

Try removing the /var/lib/gems folder 
/usr/lib/ruby/gems/
the binary installstiing
/bin/gems*
/usr/local/bin/gem*

Remove ruby totally
using apt or if source install do a dist clean

install it again build from source before doing that do this...

sudo apt-get install zlib1g-dev
sudo apt-get install libzlib-ruby

then the usual

./configure, make , make install

Then install gems 
cd /usr/src/rubygems-0.8.11
ruby setup.rb

and ur done..

HOpe this helps..

---

