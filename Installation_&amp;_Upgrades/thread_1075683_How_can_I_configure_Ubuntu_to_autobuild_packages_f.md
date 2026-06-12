---
title: "How can I configure Ubuntu to autobuild packages from apt-get source??"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by digitalbenji on 2009-02-20
Hi,
   I'm wondering if it's possible to configure Ubuntu to automatically build packages from source.  Normally, if I want to install something from source, I'd do this:```

sudo apt-get build-dep firefox

```then:```

sudo apt-get source firefox
sudo dpkg-buildpackage -rfakeroot -uc -b

```or```
sudo apt-get -b source firefox
```then:```

sudo dpkg -i package_name.deb
```

My question is this: I'd like to built my entire Ubuntu system this way, then when updates get released, have the updates automatically download, build and compile, and install.  Can this be done?  

Please don't tell me to use Gentoo also, I like Ubuntu.

I also checked out this thread: [http://ubuntuforums.org/showthread.php?t=1075683](http://ubuntuforums.org/showthread.php?t=1075683) 
I'm still curious how the effects of that will work with updates.  I'll post in that thread as well. 


:popcorn:

---

