---
title: "Need to flash bios for Ubuntu 9.10, can't use floppy or usb? Please help!"
date: 2009-12-12
forum: Hardware
---

### Post by rleggett on 2009-12-12
So, I have been scouring every forum I could find on this matter but have yet to find something that works.  First of all, I have an older Dell Dimension 8100 (Pentium 4) that I want to install Ubuntu 9.10 on (it was recently cleared of all data and OS's).  I tried installing Ubuntu last night but when I restarted the computer, I saw

GRUB loading...
ERROR 2

After reading the forums about this I found possible answers to the problem and tried as many as I could but one of them was to update the bios.  I currently have A05 but the latest bios update is A09.  Somebody said they updated to the new version and Ubuntu booted up just fine.

My problem:
I have read many of the forum responses to this and have tried everything I could find but nothing has worked so far.  I have a windows laptop as well and tried to use the support.dell.com bios updater download for a dimension 8100 but the bootable disk program opens, says it cannot find a floppy drive, and closes.  There is an unpacked version that needs to be put onto a DOS bootable disk, but I don't know how to do this since the file is an .exe

HOW do I make a DOS bootable disk from Dell's 'unpacked' bios .exe file?  I have tried Bart's way to creating bootable cd's but I couldn't get it to work. ([http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/)) If you need more info, let me know.

Thanks all!

---

### Post by paulisdead on 2009-12-12
[http://www.nenie.org/misc/flashbootcd.html](http://www.nenie.org/misc/flashbootcd.html)
This has worked for me.
If the bios is too large to actually fit inside the floppy image, what I've done is used a dos floppy image, that included cd drivers, and just had the bios and flash utility on a directory on the cd.  The directions above create a ramdisk that emulates a 1.44mb floppy.

You might just be able to run unzip on the .exe file to unpack it.  You might even be able to open it in file-roller to unpack it.

---

### Post by Daveth on 2009-12-12
flashing the bios sounds hazardous, as failure to achieve perfection hoses your system. Have you explored editing the grub menu during the boot process?

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

has some guidance. I have seen suggested that altering the hard drive numbering in that grub boot sequence has worked for some to overcome Grub error 2, and it seems worth trying that than diving straight into flashing the bios.

---

