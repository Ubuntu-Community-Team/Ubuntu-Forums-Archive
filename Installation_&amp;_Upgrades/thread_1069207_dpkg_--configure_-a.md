---
title: "dpkg --configure -a"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Taigen on 2009-02-13
Ok so I am trying to install et-linux-2.55.x86.run and yes I want 2.55 not 2.60.. Ok problem starts with I need libgtk-1.2, so I saw this on the web for installation ...

[http://ubuntuforums.org/showthread.php?t=146812](http://ubuntuforums.org/showthread.php?t=146812)

And now ever time I try and run synaptic package manager, and install the game it gets this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

which should be a solution to my problem? However in stead I received this:

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 8 package `linux-restricted-modules-common':
 EOF after field name `Auto'

I cannot access my synaptic package manager and I am new to linux so try to keep things someone simple. I have searched the web for the dpkg: parse error, but have found nothing so I decided to try a new topic. Hopefully someone can help thanks. =p

---

### Post by ugm6hr on 2009-02-13
Never had this problem - but it appears you are in good company:
[http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/](http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/)
[http://ubuntuforums.org/showthread.php?t=1022727](http://ubuntuforums.org/showthread.php?t=1022727)

---

