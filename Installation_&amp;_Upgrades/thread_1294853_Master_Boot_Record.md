---
title: "Master Boot Record?"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-10-18
Could I get input on what is the best way to backup and then restore the MBR. I hope it never happens but if it does i would like to be able to "attack" the problem with confidence. (i pratice "what if" problems with my old computers)  thanks to all... Paul

---

### Post by raymondh on 2009-10-18
> **toolmanpaul said:**
> Could I get input on what is the best way to backup and then restore the MBR. I hope it never happens but if it does i would like to be able to "attack" the problem with confidence. (i pratice "what if" problems with my old computers)  thanks to all... Paul

GRUB is my bootloader of choice.  If that borks and does not give me access to any OS installed in the HD,  I just reinstall GRUB using the ubuntu liveCD.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or, were you looking at 'cloning' your actual MBR?  I use PING to clone my HD and its' installations.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Or, see post number 2 in this thread.

[http://ubuntuforums.org/showthread.php?t=1294411](http://ubuntuforums.org/showthread.php?t=1294411)

Hope these help.  Happy ubuntu-ing.

---

