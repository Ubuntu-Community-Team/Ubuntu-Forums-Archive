---
title: "how to upgrade a program that was installed using aptitude"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by sthapit on 2009-02-22
I currently have Ruby 1.8.6 on my machine running Ubuntu gutsy that was installed using this command -

```
sudo aptitude install ruby1.8-dev ruby1.8 ri1.8 rdoc1.8 irb1.8 libreadline-ruby1.8 libruby1.8 libopenssl-ruby -y
```

ruby -v    =>    ruby 1.8.6 (2007-06-07 patchlevel 36) [x86_64-linux]

I need to upgrade to Ruby 1.8.7.  I tried doing

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

but the ruby version is still at 1.8.6.  Can someone help?  Thanks.

---

### Post by x33a on 2009-02-22
you can only update this way, if there is a newer version available in the repositories.

---

### Post by Mark Phelps on 2009-02-23
You can only update apps you installed via the repositories when those get updated -- which typically trail the new versions by weeks or months.

Some apps provide their own .deb files which you can download and update the version on your machine.  I do this with GIMP all the time.

You nearly always have the alternative to download an archive containing the source and make an executable from that -- but that requires bunches of libraries and other stuff.  You will probably also have to deal with lots of dependencies when you do that.

---

