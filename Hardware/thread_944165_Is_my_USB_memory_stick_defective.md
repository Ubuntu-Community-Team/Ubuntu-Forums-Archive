---
title: "Is my USB memory stick defective?"
date: 2008-10-11
forum: Hardware
---

### Post by pickarooney on 2008-10-11
I plug in the drive, dmesg recognises it:

```

[  837.867921] usb 3-8: new high speed USB device using ehci_hcd and address 8
[  838.001577] usb 3-8: configuration #1 chosen from 1 choice
[  838.017929] scsi6 : SCSI emulation for USB Mass Storage devices
[  838.023498] usb-storage: device found at 8
[  838.023506] usb-storage: waiting for device to settle before scanning
[  843.018563] usb-storage: device scan complete
[  843.019431] scsi 6:0:0:0: Direct-Access     USB2.0   Flsah Disk       2.20 PQ: 0 ANSI: 2
[  843.030577] sd 6:0:0:0: [sdf] 33075200 512-byte hardware sectors (16935 MB)
[  843.033671] sd 6:0:0:0: [sdf] Write Protect is off
[  843.033678] sd 6:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  843.033682] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[  843.036411] sd 6:0:0:0: [sdf] 33075200 512-byte hardware sectors (16935 MB)
[  843.037041] sd 6:0:0:0: [sdf] Write Protect is off
[  843.037047] sd 6:0:0:0: [sdf] Mode Sense: 0b 00 00 08
[  843.037051] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[  843.037058]  sdf: unknown partition table
[  843.039604] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[  843.039663] sd 6:0:0:0: Attached scsi generic sg5 type 0

```

but **lsusb** does not

Kubuntu doesn't create an icon or add anything to mount. 
If I create a /media/usb directory and manually 
```
sudo mount -t vfat /dev/sdf /media/usb
```

I can then navigate to /media/usb and krusader tells me there's 15.8GB free here, which corresponds to the size of my memory stick. I can't write to it though. Is this device DOA or is there something I can do to get Kubuntu to recognise it?

/hopes somebody will read this and it won't just disappear like all the other problems-with-mounting-in-Hardy threads

---

### Post by kidders on 2008-10-12
Hi there,

> **pickarooney said:**
> I plug in the drive, dmesg recognises it:```

[  843.037058]  sdf: unknown partition table

```

Looks like you forgot to format your memory stick.

These kinds of devices are often formatted by the manufacturer (so they work out of the box), however running commands like "mount /dev/sdf /media/usb" and attempting to write to /media/usb will have destroyed any partition table that may have been on it. One way or another, there is nothing on it now for KDE/etc. to recognise.

You'll need to (re)create a partition table, and set up a new filesystem on your memory stick to make it work.

(You should always take care with commands that start with "sudo". Don't run one unless you know what it's going to do.)

---

### Post by pickarooney on 2008-10-12
Cheers man, I gave qtparted a lash and I'm in business now. :)

---

### Post by pickarooney on 2008-10-13
Well, back to square one... I copied a file to it on a Windows machine today and when I brought it home the disk wouldn't mount any more. What's more, qtparted won't allow me to recreate a partition on it (critical error during ped_disk_new). Qtpqrted spqt the following error:

```

Error: Unable to open /dev/sdf - unrecognised disk label.
A bug has been detected in GNU Parted.  Refer to the web site of parted http://www.gnu.org/software/parted/parted.html for more informations of what could be useful for bug submitting!  Please email a bug report to bug-parted@gnu.org containing at least the version (1.7.1) and the following message:  Assertion (disk != NULL) at ../../libparted/disk.c:1319 in function ped_disk_next_partition() failed.
Error: Unable to open /dev/sdf - unrecognised disk label.
A bug has been detected in GNU Parted.  Refer to the web site of parted http://www.gnu.org/software/parted/parted.html for more informations of what could be useful for bug submitting!  Please email a bug report to bug-parted@gnu.org containing at least the version (1.7.1) and the following message:  Assertion (disk != NULL) at ../../libparted/disk.c:1319 in function ped_disk_next_partition() failed.
Error: Unable to open /dev/sdf - unrecognised disk label.
A bug has been detected in GNU Parted.  Refer to the web site of parted http://www.gnu.org/software/parted/parted.html for more informations of what could be useful for bug submitting!  Please email a bug report to bug-parted@gnu.org containing at least the version (1.7.1) and the following message:  Assertion (disk != NULL) at ../../libparted/disk.c:1319 in function ped_disk_next_partition() failed.

```

Any ideas?

I tried fdisk, cfdisk and gpart, but none of them have let me create a primary partition.

---

### Post by kidders on 2008-10-16
The partition table has probably been corrupted. Failing to unmount the disk properly after writing to it can cause corruption ... but so can a variety of other things.

To get rid of the problems re-creating a valid partition table, try erasing the first megabyte or two of your disk. That should discourage your partitioner from getting tangled up in knots trying to figure out what's on it.

```
sudo dd if=/dev/zero of=/dev/sdf bs=4096 count=256
```

Something like that ought to do the trick, but do _take care not to blindly run that_ without understanding it fully ... mistakes involving dd invariably cause catastrophic data loss.

---

### Post by pickarooney on 2008-10-17
I tried that with I think count=1000 to no avail. I might give it another go with different figures. 
I tried a few Windows utillities also, but it was unformattable there too.

---

### Post by kidders on 2008-10-18
:( It's starting to look like the disk is faulty.

Sorry I wasn't able to help.

---

### Post by pickarooney on 2008-11-14
I got a new mp3 player today, plugged it in, added a few files, accidentally plugged it out without safely removing, and the exact same thing is after happening!

F@cking OS has just killed another piece of hardware on me??

---

