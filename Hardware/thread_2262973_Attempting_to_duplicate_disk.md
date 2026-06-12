---
title: "Attempting to duplicate disk"
date: 2015-01-28
forum: Hardware
---

### Post by lsutiger on 2015-01-28
I am attempting to duplicate a disk but the system does not see the disk. There are no partitions on the disk and the disk is new.

From dmesg:
```
[26165075.960879] usb 1-1: new high speed USB device using ehci_hcd and address 84
[26165076.114151] usb 1-1: configuration #1 chosen from 1 choice
[26165076.116254] scsi34 : SCSI emulation for USB Mass Storage devices
[26165076.116487] usb-storage: device found at 84
[26165076.116492] usb-storage: waiting for device to settle before scanning
[26165081.110750] usb-storage: device scan complete
[26165081.111559] scsi 34:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[26165081.112606] sd 34:0:0:0: Attached scsi generic sg8 type 0
[26165081.115934] sd 34:0:0:0: [sdh] Attached SCSI disk

```
But fdisk -l does not show the disk. under /dev there is a file for sdh with a time stamp of the time that I plugged in the disk.

How do I get the system to recognize the disk?

---

### Post by weatherman2 on 2015-01-28
You probably need to initialize the disk.  You can do this with Gparted (if you don't have that, install it first).  First you need to create a partition table.  Then you need to create partitions.  You can do all of this in Gparted.

FYI, the old-style "MSDOS" partition structure works fine for disks that are 2.1TB or smaller.  If your disk is larger, consider using the newer GPT partition table instead (may have compatibility issues with older computers).  You need at least one partition on the disk.  You can simply make one large partition in Gparted that takes up the entire disk space.

I should ask, though: what do you mean by "duplicate the disk?"  What are you trying to accomplish?

---

### Post by wyliecoyoteuk on 2015-01-28
If you are trying to clone your existing Operating system to a new disk, then try 
Clonezilla.
Boot from the live CD or USB stick with both disks attached, then run through the disk to disk routine.

[http://clonezilla.org](http://clonezilla.org)
Just done this with my wife's PC (old disk was failing) worked a treat, and was very quick.

---

### Post by lsutiger on 2015-01-28
Thank you for the responses. I was attempting to clone a full disk into a partition on a much larger drive. I may still do that, but I will probably just do a copy.

I am currently doing a long overdue upgrade to 14.04 on my business desktop. I also am getting a hard drive upgrade.

---

### Post by weatherman2 on 2015-01-28
I recommend Clonezilla as well.  You can make an image of an existing disk/partition with Clonezilla instead of "cloning" it directly to another disk.  Then you can restore the image later with Clonezilla to the same disk or another disk.

But you will still need to initialize your new disk before you can save any files on it.  If you are going to clone your old drive completely to this new (USB?) disk, then you would not need to initialize it - Clonezilla should take care of that.

You will need to boot Clonezilla from a USB flash drive or CD or something.  You don't want to copy/clone a live or booted OS unless you are using a snapshot (I'm guessing you are not, unless you have Linux installed in an LVM right now.).

---

