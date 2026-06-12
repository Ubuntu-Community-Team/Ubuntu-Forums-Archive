---
title: "Raid 5 array has gone AWOL!"
date: 2011-10-08
forum: Hardware
---

### Post by pepsifx357 on 2011-10-08
I have a motherboard with an NVIDIA raid controller on it.  I used to use it until it became unstable.  Constantly showing the status upon POST as "Degraded."

So I decided to use the Disk Utility to create a new raid 5 with the same hard drives.

I found out that one of the hard drives failed, so I bought another one.

After about an hour waiting for it to finish syncing the new drive.  Another one failed.

I used the disk utility to stop the array and find the problem.  Turns out there is one (1) bad sector on another disk.

Now I can't do anything.  I can't format, I can't erase, I can't mount, I can't umount, I can't delete any partition on any drive in the array.  I also can't start the array back up.

If I try to do any of these things listed above I get this:

ERROR FORMATING DRIVE:

```
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/sdb: Device or resource busy
```

OR

ERROR DELETING PARTITION:

```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=32256
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=4
refusing to delete a protected partition
```

OR

ERROR STARTING RAID ARRAY:

```
Error assembling array: mdadm exited with exit code 1: mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted

```

Whats the deal?

---

### Post by LinuxFan999 on 2011-10-08
What brand and model is your motherboard? How old is it?

---

### Post by pepsifx357 on 2011-10-08
> **LinuxFan999 said:**
> What brand and model is your motherboard? How old is it?

ASUS A8N-32-SLI

It's about 6 years old.

---

### Post by pepsifx357 on 2011-10-11
I just replaced the drives.  They seem to be doing good now.

---

