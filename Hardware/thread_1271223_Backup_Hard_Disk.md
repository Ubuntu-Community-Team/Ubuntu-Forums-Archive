---
title: "Backup Hard Disk"
date: 2009-09-20
forum: Hardware
---

### Post by nshiell on 2009-09-20
I have a PC running Ubuntu.
The primary drive is the OS drive (the drive that boots Ubuntu)
And a secondry drive that holds the data
The machine has started acting unpredictably so I wanted to remove all my data from it.

I took out my data drive and put in my other desktop, when I connected it, "Grub" didn't know how to boot from my other desktop with 2 drives?

Got error "**Error Loading Operating System**" (Grub?)
So when I booted from my Ubuntu CD the live CD booted fine but couldn't mount the drives.

So my solution:
1. connect my data drive and boot from live CD.
2. double click on the drive (so Ubuntu mounts it)
3. Connect up an external USB drive and double click that to mount it
4. Goto terminal and do ```
sudo cp /media/disk /media/disk-1 -rfp
```

**TAKES AGES VIA USB, so if your disk is about to die this is not the best way to do it.**

Why is Ubuntu not able to mount both drives and boot ok?
Why is Ubuntu not giving me writing rights to the drives? - except as root?

---

### Post by mikewhatever on 2009-09-20
Booting from an hdd and mounting an hdd is not the same. When several hdds are present, the order they are seen by both GRUB and BIOS matters. Perhaps the computer was trying to boot from the newly installed hdd or looking for the OS on a wrong partition.

The main purpose of running from a live cd is testing the hardware. To prevent easily deleting valuable info by mistake disk access is root only.

---

### Post by sad1sm0 on 2009-10-24
If you haven't already figured out your problem, you might want to double check to make sure that the dip switches are configured correctly for your hardware setup.  Moving a drive from one box to another sometimes requires changes to be made depending on existing hardware and such.  If you are having trouble seeing the disks from the live cd, this is where I would check.  BIOS settings also control what the boot order is, so you may need to make changes there as well.

---

