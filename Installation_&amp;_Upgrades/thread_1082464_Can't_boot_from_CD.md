---
title: "Can't boot from CD"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by corncob on 2009-02-27
I'm trying to install Intrepid in my daughter's PC but can't get the CD to boot.  I'm getting the message: 
No Emulation.
ISOLINUX 3.63 Debian-2008-07-15 isolinux Disk error 80, AX=4240, drive 9f
Boot failed: press a key to retry...
The computer seems to be hung at that point and all I can do is turn it off.
I tried to boot it from the 2nd CD drive (I did change the boot sequence in the BIOS appropriately) but it goes straight to Windows.  Can anybody tell me what's wrong and what I can do about it?  The computer does have a second HD on which Ubuntu had already been installed but got totally messed up.  It was the boot drive at the time and wouldn't boot so right now the boot drive is set to the Windows HD in BIOS.

---

### Post by taurus on 2009-02-27
Have you tried to boot the same disc with another machine to make sure it is not the disc?

Otherwise, here are a few things that you can do to make sure you have a working/bootable Ubuntu CD.

1.  Run a checksum to check the integrity of the ISO image after you've downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Burn it at a slow speed like 4x.

3.  At the initial menu from the CD, run the check cd for defects option to make sure the CD is good.

---

### Post by albinootje on 2009-02-27
> **corncob said:**
>  I tried to boot it from the 2nd CD drive (I did change the boot sequence in the BIOS appropriately) but it goes straight to Windows.

If installing from cdrom keeps on failing, you can consider installing from an usb stick :
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by corncob on 2009-02-28
I'm going to work on it some more today.  I had booted with that CD (actually a DVD with Ubuntu Ultimate) from that same drive a couple hours previously and installed a fresh copy in the computer in addition to the one already there.  However, this did not fix the problem it was having (blank lines in place of menu items in Openoffice and AbiWord) so I deleted the partition thinking that I would reinstall it once more but this time without importing her settings.  That's where I messed it up -- it wouldn't even get to the grub menu.  I don't see what this has to do with booting the live disk though.

---

### Post by taurus on 2009-02-28
From what you've described in your OP, it sounded like your machine wouldn't boot from the LiveCD.  That's why I thought there was a problem with the CD (or DVD, whichever one you use).

---

### Post by corncob on 2009-02-28
I restored the boot loader with Super Grub ([http://www.supergrubdisk.org](http://www.supergrubdisk.org)) which got my original system back (whew!).  Still, although I got to various stages, I wasn't able to finish installing that second copy of Ubuntu until, after trying everything else, I booted the disk from the second DVD drive and it went to completion without errors.  Looks like I need a new DVD drive (those disk cleaners didn't help).  Thanks guys.  I'll mark this thread as solved.

---

