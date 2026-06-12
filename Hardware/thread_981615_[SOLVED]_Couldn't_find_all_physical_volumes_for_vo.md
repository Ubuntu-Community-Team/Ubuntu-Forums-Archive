---
title: "[SOLVED] Couldn't find all physical volumes for volume group"
date: 2008-11-13
forum: Hardware
---

### Post by Phydeaux on 2008-11-13
I just can't seem to leave well enough alone.  Was running mythbuntu 8.04 and decided to upgrade to 8.10.  All did not go well, and for some reason decided to wipe out the / partition, leaving the lvm intact.  Long story short, I think it knows that I have the lvm there, though I'm not sure it sees it spanning both HDs.  Here are some setups:
```
 cat /proc/partitions
major minor  #blocks  name

   8     0  488386584 sda
   8     1    3116578 sda1
   8     2     787185 sda2
   8     3  484480237 sda3
   8    16  488386584 sdb
   7     0     577256 loop0

```
```
 vgscan
  Reading all physical volumes.  This may take a while...
  Couldn't find device with uuid 'xxxx'.
  Couldn't find all physical volumes for volume group vg.
  Couldn't find device with uuid 'xxxx'.
  Couldn't find all physical volumes for volume group vg.
  Volume group "vg" not found

```
```
pvscan
  Couldn't find device with uuid 'xxxx'.
  Couldn't find device with uuid 'xxxx'.
  PV unknown device   VG vg   lvm2 [465.76 GB / 0    free]
  PV /dev/sda3        VG vg   lvm2 [462.03 GB / 0    free]
  Total: 2 [927.79 GB] / in use: 2 [927.79 GB] / in no VG: 0 [0   ]

```
```
 fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005fcf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         388     3116578+  83  Linux
/dev/sda2             389         486      787185   82  Linux swap / Solaris
/dev/sda3             487       60801   484480237+  8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```
xxxx is obviously the old UUID, I'm not sure if that's sensitive data.  Plus I wanted to shorten this.
Disk sdb is the other drive, which supposedly has the 'second half' of the LVM.  These commands are being run from the livecd, I read I need to run it from there to do any serious restoration.
The LVM contains /var/lib if that makes any difference.  Everything else has been formatted.  I wouldn't care so much if there wasn't nearly a terabyte of dvd's on there :)  Any help or direction would be greatly appreciated.

---

### Post by Phydeaux on 2008-11-14
I should also note that webmin does have a drive Id that is the same string size for this partition, is that what the new uuid should be?  Can I just change what it thinks it is?

---

