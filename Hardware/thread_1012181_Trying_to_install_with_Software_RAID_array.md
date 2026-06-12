---
title: "Trying to install with Software RAID array"
date: 2008-12-15
forum: Hardware
---

### Post by orangejon on 2008-12-15
I just discovered to my dismay that my supposedly-RAID card is in fact a "fake", so it looks like I'll have to use Software RAID.

[This thread]("http://ubuntuforums.org/showthread.php?t=408461") says that I can use the "alternate" CD to set up a software RAID array during installation.  However the "alternate" installer gives an error during the "Detect Disks" step.  The error on the console is "ERROR: sil: RAID type 253 not supported".

I tried using the normal (Live CD) version and issuing the commands mentioned at the bottom of the post (mdadm --create etc.), which seem to work, but then I run the "ubiquity" installer and the drives are still displayed individually.

The drives are 3 identical 1TB SATA drives connected to a Silicon Image 3114 controller, with msdos partition tables and a single unformatted partition on each.

---

### Post by elvinatom on 2008-12-15
what layout did you plan for you 3 disks? (partitions, mountpoints ...)

---

### Post by ScaryBob on 2009-07-06
Do not define a RAID array in the Sil 3114 controller firmware. (If one is already defined, delete it.) The drives must be seen as individual SATA drives for software RAID to use them. This will cause a 'no devices found' error on boot. Just ignore it. I would also remove any existing partitions. Fdisk the individual drives and create a full disk Linux Software RAID partition on each. Then create the MD0 device.

---

