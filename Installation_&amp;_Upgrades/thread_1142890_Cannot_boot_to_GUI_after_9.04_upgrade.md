---
title: "Cannot boot to GUI after 9.04 upgrade"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by brons2 on 2009-04-29
Hello,

I cannot boot into the Gnome gui after upgrading to 9.04 on my desktop.  The upgrade installed fine on my laptop, but on my desktop the computer hard-locks with some garbled display on it.  If I tell it to boot with no GUI, it seems to work fine but I'm a GUI guy.

I do have an ATI HD4850 on this machine and I did have the closed-source ATI drivers on it before upgrading, perhaps I should have gone back to the generic video drivers before upgrading.

Anyways, I would really just like to be able to boot up to the desktop.  Is there any way to reset all the video options back to defaults.

BTW - the Windows partitions on this machine work fine so I don't think it's any sort of hardware problem.

---

### Post by brons2 on 2009-04-29
Oh and I have tried the Recovery dealie.  I boot up to the Recovery Menu, and have options for resume, clean, dpkg, fsck, grub, netroot, root and xfix.  I've tried the xfix a couple of times with no result.  (argh)

---

### Post by silentknyght on 2009-04-29
Try force-booting into safe graphics mode, whereupon you can download/install fresh/new drivers?  The information here may be useful:

[http://ubuntuforums.org/showthread.php?t=438486](http://ubuntuforums.org/showthread.php?t=438486)

---

### Post by brons2 on 2009-04-30
> **silentknyght said:**
> Try force-booting into safe graphics mode, whereupon you can download/install fresh/new drivers?  The information here may be useful:

[http://ubuntuforums.org/showthread.php?t=438486](http://ubuntuforums.org/showthread.php?t=438486)

None of the stuff in that thread works :(

---

### Post by brons2 on 2009-04-30
Fixed it by dropping down to the terminal prompt with networking, from the recovery menu.  From there typed in sudo apt-get remove xorg-driver-fglrx.  That removed the proprietary ATI driver for my card.

No acceleration is kind of a bummer but oh well.

---

