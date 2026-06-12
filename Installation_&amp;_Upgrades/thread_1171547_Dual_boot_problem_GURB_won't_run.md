---
title: "Dual boot problem GURB won't run"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by jfrelin on 2009-05-27
My computer has ubuntu (Jaunty) installed on a USB hard drive and Windows XP pro on the C: (it was installed first).  When I power on the computer the GRUB Loader screen flashes and I get a Error21 that I guess means it can't find the rest of GRUB.  If I CTL-Alt-del usually the GRUB will load fine, and I can choose the OS to boot.  Everything works fine from here on.  

When I restart, I almost always have the same problem as power on and need to CTL-ALT-DEL to get the OS choices

OK so annoying.  When I installed VMware and try to power on it shows a disk not found error, so I assume there is still a problem looking for the GRUB file where its not.

Any ideas on how to fix this?  C: is NTFS and the USB is ext3.

:(

---

### Post by linesma on 2009-05-27
It sounds like GRUB is corrupted.  The following link will tell you how to restore GRUB and make it work properly.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")

Granted, this tutorial is for installing Win XP on a machine that already has Ubuntu installed, but I have successfully used this tutorial to repair my GRUB, dual boot with Ubuntu and Win XP, after a power failure.

I hope this helps,

linesma

---

