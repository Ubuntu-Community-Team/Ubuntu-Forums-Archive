---
title: "Dual-Booting with multiple Windows OS's"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by rla128 on 2005-07-22
I know that I can dual boot Windows XP and Ubuntu, and it works fine.  I used this guide, by the way:  [http://www.ubuntulinux.org/wiki/WindowsDualBootHowT](http://www.ubuntulinux.org/wiki/WindowsDualBootHowT)

Once I do this, I'm wondering, is it possible to install other Windows OS's, such as Windows 2000 and Windows 98, and have them be handled by the boot manager as well?

This is obviously for testing software and whatnot across several OS's.

Anyone have any experience with this?

---

### Post by pressureman on 2005-07-22
[QUOTE=rla128]I know that I can dual boot Windows XP and Ubuntu, and it works fine.  I used this guide, by the way:  [http://www.ubuntulinux.org/wiki/WindowsDualBootHowT](http://www.ubuntulinux.org/wiki/WindowsDualBootHowT)

Once I do this, I'm wondering, is it possible to install other Windows OS's, such as Windows 2000 and Windows 98, and have them be handled by the boot manager as well?[/QUOTE]

From memory, Windows XP and 2000 don't care where on the hard disk they are installed (ie, primary/logical partition), provided that NTLDR is on a primary partition marked as active. Using GRUB as the boot loader probably relaxes this problem (and GRUB's partition needs to be marked as bootable/active anyway).

Windows 98 however, being largely a legacy DOS spinoff, must reside on the first primary partition of the first hard disk on a system.

If you only need to run multiple OSes for testing purposes, and performance is not a top priority, you may find using VMware more convenient (it is a commercial product however).

---

### Post by rla128 on 2005-07-23
Can I get a confirmation here?

---

### Post by pressureman on 2005-07-23
[QUOTE=rla128]Can I get a confirmation here?[/QUOTE]

I personally run Windows XP and Ubuntu Linux on my laptop. Windows C: and D: drives are /dev/hda1 and /dev/hda2 respectively, Linux root partition is /dev/hda3 and swap is /dev/hda5.

I use GRUB to switch between Windows and Linux. No problems whatsoever.

---

