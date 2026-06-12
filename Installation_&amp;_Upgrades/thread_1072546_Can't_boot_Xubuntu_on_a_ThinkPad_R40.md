---
title: "Can't boot Xubuntu on a ThinkPad R40"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by brons2 on 2009-02-17
I have installed Xubuntu on a IBM ThinkPaid R40.  In fact I have been through the CD install twice.  After I install it, everything appears normal, but it then refuses to boot.  It will go through the whole process but then just say "Operating System Not Found".

The funny thing is, when I put the CD in and boot from that, the first thing it does is come up to the menu where it offers to boot from LiveCD, install, run a memory test, etc.  From that menu if I choose to boot from the primary hard drive, then it works and I am able to successfully boot from the hard drive.

Anyone seen this before?  The hard drive is first in the boot order in the BIOS, by the way.

---

### Post by dstew on 2009-02-17
I think what is happening is that the boot loader on the Live CD is able to boot your hard drive, but the hard drive itself, together with the computer's BIOS, cannot boot. This could be due to a BIOS setting problem, or that there is no boot loader installed on the hard drive.

Did you install grub when you installed Ubuntu? If you are not sure, you can [install grub from the Live CD]("http://ubuntuforums.org/showthread.php?t=224351"). For a more in-depth analysis of your boot problems, you can download to the Live CD file system [this boot analysis script]("http://sourceforge.net/projects/bootinfoscript/") and run it. See [this thread]("http://ubuntuforums.org/showthread.php?t=1072554") for an example of this script being used to solve a boot problem.

---

### Post by brons2 on 2009-02-17
The hard drive had a bang mark in front of it in the BIOS boot order settings.  I don't know what that was about, but I went ahead and did an F9 to reset the BIOS to factory configuration and that was successful, I was able to boot from the hard drive on the next attempt.

---

