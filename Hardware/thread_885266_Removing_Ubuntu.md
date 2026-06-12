---
title: "Removing Ubuntu"
date: 2008-08-09
forum: Hardware
---

### Post by oldtom on 2008-08-09
Hi All,
I had Ubuntu installed on a single partition on my laptop. I wish to reinstall XP pro and then dual boot. However, I've run into trouble and seek assistance please.

I used a live edition of Ubuntu and Gparted to reformat my drive back to the NTFS file system. The partition is called /dev/sda1, but I can't rename it. There was also an extended partition called /dev/sda2 and a linux swap file called /dev/sda5. These were wiped of course, when I reformatted to NTFS and now I can see the whole drive formatted as NTFS, but still named /dev/sda1. But from here I'm lost.

When I use my XP to setup windows, no drives are recognised except a FAT32  stick plugged in to my usb port. I have previously and successfully installed XP within Ubuntu using virtualbox, so my installation disk is intact and it accepts my product key ok.

Does anyone know what I'm doing wrong. If my XP setup disk can't see my NTFS formatted drive, obviously I can't install windows. :confused:

Thankyou in advance for any help you can give me.

Regards,
Richard

---

### Post by cdtech on 2008-08-09
You should format using vfat and your windows will see that.

---

### Post by cariboo on 2008-08-10
Your Windows installation cd should see the drive, but it may not be able to read it. If you see a partition of any sort, just delete it and create a new partition the size you think you'll need to run windows and leave the rest of the drive unpartitioned. When its time to install ubuntu use the unpartitioned part of the drive.

Jim

---

### Post by jocko on 2008-08-10
Have you ever installed windows on that computer (except in a virtual machine)?
It could very well be that windows doesn't have the correct drivers to access your hard drive. Which motherboard does your computer have? It may be that you have to get some drivers from the manufacturer and have the windows installer load them before it can see the hard drive.

As an example, my desktop have a Gigabyte 7nnxp motherboard, which have three different technologies for connecting hard drives:
1. "Normal" ata-66/100 (nvidia), windows xp recognizes this without problem.
2. ata-133 raid chipset (ite), the windows installer requires a driver install floppy from ite before it's possible to install xp on a drive attached here.
3. sata raid chipset (silicon image), don't know if windows recognizes this. I dumped windows before I got a sata drive, but I doubt xp have the drivers for this built in to the installer.
So why did XP not have support for my ata raid chipset? Because XP is an antique os that was developed before the raid chipset on my computer, so MS didn't know about it.
(XP was released in 2001, my motherboard in 2003).
But, I guess microsoft adds such important hardware drivers to the service packs, so that installation cds with integrated service packs will support newer hardware.

So try to find out exactly what ata or sata chipset your hard drive is connected to, and try to see if you can find any windows drivers for it. Then you should be able to install xp by pressing F6 when the installer is loading (I think it says something like "Press F6 to install scsi or raid drivers" or something similar) and have the drivers loaded from a floppy (don't know if it can be done without a floppy... as I said, XP is an antique os).

---

