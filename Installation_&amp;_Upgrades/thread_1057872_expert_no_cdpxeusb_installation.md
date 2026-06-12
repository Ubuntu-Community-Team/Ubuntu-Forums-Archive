---
title: "expert no cd/pxe/usb installation"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Noremacam on 2009-02-02
This one is for the geniuses. I have a laptop that had a blank hard disk. The cd rom is broken, and the bios doesn't support usb booting of any type. PXE netboot doesn't seem to work either(I've tried different methods and OS's). Yes, I'm competent in PXE booting.

The only method I have right now for installing an OS is taking out the hard drive and putting it in an external usb drive I have lying around.

I originally tried hooking up that drive into my desktop and installing Ubuntu onto it and then putting it back into the original laptop but it hung on startup on the sata driver(and its an ide drive). So I could never get to a prompt on the installation I have.

Is there a way to get Ubuntu onto the drive without it doing the hardware detection until the first boot - or is there another method that seems obvious to you? This is such an unusual problem I wouldn't be surprised if there wasn't an answer but any  help, even if its extremely unintuitive, would be extremely appreciated.

---

### Post by boof1988 on 2009-02-02
One (similar to your method) way I have used (I'm sure there are more elegant solutions) is the following:

[LIST=1]
[*]Hook the HDD up to a working computer (which has Unetbootin, a partition manager and the iso installer file).
[*]Create an "Installer" partition on the drive.
[*]Use Unetbootin to copy the iso onto the partition and make it bootable.
[*]Reinstall the HDD into target machine.
[*]Boot and cross fingers.
[/LIST]

This has worked (for me) using Ubuntu/Xubuntu 8.04 but hasn't worked for 8.10.  So if you are installing 8.04 it may work.  It you're installing 8.10 then maybe a less chance of working.  Other distros, I haven't tried yet.

I'm sure there will be other ideas that will be better than this.  So I look forward to seeing how you get it installed.

---

