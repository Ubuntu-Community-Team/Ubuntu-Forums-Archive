---
title: "Pre-install clean up -- I WANT to deletemy data, but I can't"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-03-03
I am attempting to install (re-install) Ubuntu on a system with a lot of hard disks. My previous attempts failed due to grub issues, but I understand those issues better now thanks to this forum. So I'm ready for a full installation with LVM, crypto and multiple disks.

As I start to plan this install, I'm looking at the output of several utilities (such as boot_info_script).

I'm noticing errors on a couple of the disks. The errors are summarized as:
1. vgscan reports "Incorrect metadata area header checksum" on two disks
2. "Invalid MBR Signature found" on one disk by boot_info_script.
Also, the installer reports that it has found a raid set (which it should not).

Since there is nothing important on these disks right now, I deleted the partitions and started with completely free unpartitioned space. But the errors persist no matter what I try (so far).

I have tried removing "everything" with various tools.

Now, vgscan doesn't show any LVs or groups on these disks
and ...
```
dmraid -r
No RAID disks
```

but the errors remain

Drive: sde
```

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000377d3

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63       690,794       690,732  83 Linux
/dev/sde2             690,795 1,953,520,064 1,952,829,270  83 Linux

```


```
vgscan      /dev/sde: size is 1953525168 sectors
vgscan      /dev/sde1: size is 690732 sectors
vgscan      /dev/sde1: size is 690732 sectors
vgscan      /dev/sde1: lvm2 label detected
**vgscan  Incorrect metadata area header checksum**
vgscan      /dev/sdf: size is 1953525168 sectors
vgscan      /dev/sdf: size is 1953525168 sectors
vgscan      /dev/sdf: No label detected
```

Drive: sdf 
```
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

**Invalid MBR Signature found**

```

I want to delete the metadata and/or MBR signatures from sde1 and sdf before continuing with this install. 

How can I do that?

---

### Post by cosine352 on 2009-03-03
did you tried 'partition Editor'? It comes with the Ubuntu installation CD.

---

### Post by dabl on 2009-03-03
If you want to overwrite the MBR, you need to study up on the dd command.

First "dd" the drive (using the command in accordance with the manual), then use GParted or Parted Magic to make partitions and filesystems.

---

### Post by MountainX on 2009-03-03
I have been studying dd -- it doesn't (or hasn't yet) done the trick.

I have used ```
dd if=/dev/zero of=/dev/sdX bs=446  count=1
```
and 
 ```
dd if=/dev/zero of=/dev/sdX bs=1k  count=1
```

I have also been using gparted and cfdisk. I have deleted all partitions on the drives in question with either of these partition editors, but the errors persist.

What else can I do?

---

