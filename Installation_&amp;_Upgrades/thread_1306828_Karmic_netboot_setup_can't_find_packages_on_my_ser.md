---
title: "Karmic netboot setup can't find packages on my server"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by KingStill on 2009-10-30
I am attempting to install Karmic on my laptop from a windows xp machine running Tftpd32 and apache to facilitate network booting from the alternate i386 iso. I have the iso mounted with Alcohol and tftpd/pxe successfully bootstrapped it. For ubuntu archive, I pointed the installer to my apache server (192.168.1.100) and the /ubuntu folder and it went off without a hitch until I had to select which packages I want to install (this is past partitioning). I selected ubuntu-desktop, I receive the message waiting for headers and then this:
[http://192.168.1.100](http://192.168.1.100) karmic/main xulrunner-1.9.1-gnome-support 1.9.1.3+build1
404 not found

I attempted to apache alias the karmic/main folder to isoroot/dists/karmic/main to try to trick it, but it doesn't work. 

On another note, if you can help me fix this, should I also pick different packages to install for a default vanilla ubuntu desktop installation, like the one obtained from the default desktop iso installation? Thanks in advance.

---

### Post by KingStill on 2009-10-30
I've checked my apache logs and it turns out the iso image has file names truncated to 64 characters. Is there any way to fix this?

---

