---
title: "Black screen of death 9.04"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by libertao on 2009-04-30
First time linux user here.  I've installed 9.04 about 3-4 times over the past week and always end up with a black screen with a color pixelated bar that won't load into Ubuntu.  

Directly after install, things seem to be working fine.  Then I do a restart, and it still loads fine, and then I add medibuntu repository (following this tutorial: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) ) along with a few other programs from the add programs menu including the ati driver, compiz and some others.  I've also added some codecs and programs following this tutorial:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) (not sure if I've done that every time, but possibly).  Then I restart to see the changes and...black screen.   

I know the definition of insanity so I don't want to do the same thing over again, but I'm not sure what to do differently.  Should I go with ext3 instead of ext4?  Is this something Compiz has been known to cause? Should I ignore one of those tutorials?  I am running a Dell e1505 with ATI x1400 graphic card and dual-booting with Windows7 if that helps.

Thanks!

---

### Post by Bruce S on 2009-04-30
Libertao,

     I am not an expert, but I read on a forum discussion, just a few minutes ago that ext 4 is unstable and that ext3 should be used.

     ext4 is supposed to become stable for the October release of Ubuntu.

---

### Post by libertao on 2009-05-08
Well I wouldn't say I've 'solved' the problem, but I've narrowed it down to the ATI drivers.  Any time I try to update the drivers to proprietary or restricted drivers whether manually or through something like EnvyNG, I get the black/red screen and have to reinstall.

---

### Post by wpshooter on 2009-05-08
> **libertao said:**
> Well I wouldn't say I've 'solved' the problem, but I've narrowed it down to the ATI drivers.  Any time I try to update the drivers to proprietary or restricted drivers whether manually or through something like EnvyNG, I get the black/red screen and have to reinstall.

It has been my experience that if you change the ATI video drivers to anything other what is installed by the O/S by default, then you are probably making a mistake !!!

---

### Post by blackSP on 2009-05-08
Not necessarily true. I installed ati-driver-installer-9-4-x86.x86_64 for my mob radeon hd2400 and everything now works fine but DON'T enable the driver in hardware drivers.

It is enabled, sysinfo tells me so.

---

