---
title: "[kubuntu too] Updated to 9.04 no graphic interface, no way to downgrade :("
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by blackzafiro on 2009-05-12
Hello,

This time I really messed up by trying the latest upgrade.  I have a 4 years old computer, Averatec, AMD Athlon XP-M 2000+, 512 MB ram, 40GB Hard drive, nothing special for graphics.  The only way I was able to install an decent Ubuntu version was to install 4.10, upgrade to 6.06 and then to 8.04.  I was required, against my will to upgrade to 8.10, the upgrade was not so clean, but after upgrading to a new kernel version it was more or less working.  I dreamed that, probably, with 9.04 I would finally have a decent working version (naive).   Now I don't have a graphic interface anymore.  At the begging it was not a surprise, it has always happened to me with this computer, usually after modifiying /etc/X11/xorg.conf by hand it would work just fine, however this time it doesn't make any difference.

When starting with the newest kernel (2.6.28-12) I don't even get any error message, it just goes to the text version.  If I try with 2.6.27-13 I get: 
```

usplash: No usable theme found for 1024x768
screen init failed
```Does this message provide any usefull information? May I just install something extra and it will work? Or is it a false hint and I am just as jammed as those with ATI cards?

Thanks for your help.

---

### Post by blackzafiro on 2009-05-12
It seems I got the same problem than:

[http://ubuntuforums.org/showthread.php?t=1135585&page=2](http://ubuntuforums.org/showthread.php?t=1135585&page=2)

---

### Post by blackzafiro on 2009-05-15
:popcorn:

Solved.  After reporting the bug in [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/376567](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/376567),

they gave the answer:
[http://www.openchrome.org/trac/changeset/738](http://www.openchrome.org/trac/changeset/738)

It is enough to have an openchrome version from or above the 738 revision.  I got it from;
[https://launchpad.net/ubuntu/karmic/i386/xserver-xorg-video-openchrome/1:0.2.903+svn741-1](https://launchpad.net/ubuntu/karmic/i386/xserver-xorg-video-openchrome/1:0.2.903+svn741-1)

Just downloaded de .deb and with >>dpkg -i [package name]<< from my working terminal it got correctly replaced :D.

Now I have a working :KSJaunty.

---

