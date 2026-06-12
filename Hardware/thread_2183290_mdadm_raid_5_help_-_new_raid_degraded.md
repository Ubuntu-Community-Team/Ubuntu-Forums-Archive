---
title: "mdadm raid 5 help - new raid degraded"
date: 2013-10-24
forum: Hardware
---

### Post by bsautner on 2013-10-24
I've setup a few raids on ubuntu before without issue.  I'm trying to spin up a quick one with two new 2TB drives on a raid 5 on ubunbu 13.10 

I ran badblocks on both drives to see if they were ok:

```
Checking blocks 0 to 1953513542
Checking for bad blocks (read-only test): done  
Pass completed, 0 bad blocks found. (0/0/0 errors)
```

I tried ext4 and xfs filesytems

Here is how i assembled the raid which worked without error:

```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=2 /dev/sda1 /dev/sdb1
```

i was able to format /dev/md0

when i reboot, i'm alerted that the raid is degraded and dropped to a initramfs rescue prompt. 

The only difference today is that these new drives needed their partitions created with **gdisk** instead of **fdisk** because fdisk reported: 

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```
The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.
```

which i'm lead to believe means that fdisk on ubuntu 13.10 doesn't understand a new standard in large drives with a large block size (or something) gdisk seemed to handle it ok.

any advice would be appreciated.

---

### Post by SaturnusDJ on 2013-10-24
The minimum for non-degraded RAID5 is 3 disks.


You probably have 4k sector disks.

Use this command to check if the 4k align is setup correctly:
```

parted /dev/sda align-check m 1

```
m = minimal, checks for 4k alignment.
o = optimal, checks for 1M alignment.

1 = partition number on device.

---

### Post by bsautner on 2013-10-24
thanks a bunch, i didn't know about the disk limit but it makes perfect sense.  reduced my raid level and things are just fine.

---

