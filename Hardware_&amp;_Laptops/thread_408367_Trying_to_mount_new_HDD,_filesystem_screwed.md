---
title: "Trying to mount new HDD, filesystem screwed"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by Nesnej Trick on 2007-04-13
I bought a second-hand Maxtor 120GB SATA drive today. I had some trouble getting my computer to find it since the on-board SATA controller was by default off, but finally I managed to get my computer to recognize it.

My Ubuntu 6.06 installation, however, seems to have trouble finding it. I first tried to format it as JFS, but the process hung itself. I killed the process and formated it as ext3 instead (It used to host an empty NTFS partition). I tried to make my system recognize it at boot by adding a line to fstab, but upon a reboot, I got the following message:
```
fsck.ext3: Bad magic number in super-block at attempt to open /dev/sda
/dev/sda:
Superblock could not be read or does not describe a valid
ext2-filsystem.
```

It appears the filesystem is corrupt. This partition didn't contain anything, so it's not much of a loss, but I'd like to be able to properly mount it, transfer my /home directory to it and use it as my new home directory after a fresh install. It also seems that there is 2.7GB of empty space at the beginning of the drive, which to me seems like a waste of space. I'd actually like to delete all partitions on this drive and start from a clean slate. What would be the most convenient manner of doing this?

---

### Post by Salpiche on 2007-04-13
why don't you repartition the drive using gparted? delete all partitions and create one, that might help correcting the problem. I usually do that with all drives before I put them on my servewr or any of the other stations.

---

### Post by moixa on 2007-04-13
maybe the partition table is screwed?
yea, as suggested before, use gparted
or zero out the entire drive see if it changes anything
dd if=/dev/zero of=/dev/harddrive

---

### Post by Nesnej Trick on 2007-04-13
I'll try that and report back.

Edit: Yes, that did the trick. Thanks a lot!

---

