---
title: "Want to move 11.10 on SSD to new PC Dell Inspirion 660s"
date: 2012-07-03
forum: Hardware
---

### Post by FundKing on 2012-07-03
Just bought a PC -Dell Inspirion 660s. Had 11.10 on Intel 120gb SSD, on Dell dimension C521.
I want to keep Windows on the HDD, and boot into Ubuntu from the SSD. The bios can see the SSD, but when I change the boot order, the screen is black w/ the cursor flashing.

I don't want to reformat or reinstall the SSD. If anybody can post a link as to how to update grub, or modify the windows bootloader, that would be great.

noob speak please - I am not that fluent in Ubuntu.

Many thanx!

---

### Post by ahallubuntu on 2012-07-03
So you had a dual boot situation on the Dimension C521?  Windows on the hard drive, Ubuntu 11.10 on the SSD?

When you installed Ubuntu 11.10, can we assume you used Grub to boot either Windows or Ubuntu?  Or did you set things up differently?  If you used Grub to boot either, Windows won't boot anymore without a repair to the boot sector (easy to do by booting a Windows disc though, get into a command prompt and type "fixmbr" for XP or "bootrec.exe /fixmbr" for Vista or Windows 7).

As for Ubuntu 11.10 separately on the SSD: it sounds like you need to re-install Grub.  For that, you'll probably need a live CD (or live USB) of Ubuntu 11.10 .  Install (physically) the SSD on the new computer and boot Ubuntu 11.10 live and then fix Grub.  I prefer the "chroot" method to update/re-install Grub.  But it requires typing a few commands in a terminal:

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

Has worked many times for me.

---

### Post by oldfred on 2012-07-03
If you are just getting black screen or screen with just cursor, you may have booted thru grub but have a video issue or other boot parameter.

What video card do you have? Is it different than the old system? I went from an old nVidia to a new one and it just worked, but if you change then you will have the wrong video driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

