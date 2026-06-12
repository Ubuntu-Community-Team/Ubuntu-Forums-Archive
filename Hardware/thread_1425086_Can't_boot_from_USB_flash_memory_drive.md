---
title: "Can't boot from USB flash memory drive"
date: 2010-03-08
forum: Hardware
---

### Post by rockhoppe7 on 2010-03-08
Hi, can anyone help?

I'm trying to boot my pc from a USB flash drive, but my computer just ignores the memory stick and boots from the first HDD installation.

I've been in to BIOS and changed the boot order so that "Removable Drive" comes before "HDD" which comes before "CD/DVD drive"  (The only other option is "NVIDIA network boot" or similar).

I've tested the USB stick on another computer (a netbook) and it boots from it perfectly. There the BIOS options are (something like) "USB drive", "Removable drive", "HDD", "network".

Is it possible that "Removable Drive" option on my pc DOESN'T include USB flash drives?  That seems unlikely, but I noticed that it doesn't explicitly offer "USB flash drive" as a boot option.

BTW - I'm trying to boot the desktop pc using the Netbook Remix version of Koala (it's just what I have available on the memory stick) - that shouldn't make a difference, should it?  I just want a temporary working system running in RAM...

Any ideas? Thanks

---

### Post by wilee-nilee on 2010-03-08
Look on the web to see if your computer should have usb boot capability.

---

### Post by rockhoppe7 on 2010-03-11
Solved this one.  My BIOS seems to be odd - it only detects the USB drive if it's plugged in on power-down before reboot.  Then it detects it on the next reboot.

I also found I had to enable "USB 2.0 drive" in the Hard Disks page as well as the Boot Sequence page - hard to do this unless they are plugged in, because the PC doesn't remember them from session to session.

So: while the system is up, insert USB drive and wait for the drive to be recognized.
Reboot, go into BIOS, enable USB Drive in Hard Disks priority AND Boot Order pages, save and exit
Which causes reboot from the Flash Drive...

To reboot back into the normal installation now also causes a problem, because I can't Shut Down and then select 'Boot from First Hard Disk' as you would normally - the USB Flash Drive is now set as the First Hard Disk (in Hard Disks priority, above).

So before rebooting, I pull out the Flash Drive, and then it sees the normal HDD as the First Hard Drive.

Bit of an ugly workaround, but works for me...

---

