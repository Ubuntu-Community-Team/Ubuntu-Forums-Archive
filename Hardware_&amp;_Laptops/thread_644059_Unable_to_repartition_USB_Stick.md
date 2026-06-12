---
title: "Unable to repartition USB Stick"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by mrc_001 on 2007-12-18
Since I erased a USB stick with OS X Leopard I can not create a new partition table (the stick is completely empty, no partition table, no partition). I tried it with parted, qtparted and gparted. Recently gparted doesn't even recognize the device.

I own the following device:
Imation USB Flash Drive
Capacity: 995 MB
Length in Sectors: 2037760

**Error when using qtparted:**
Dialog Window:
```
Critical error during ped_disk_new!/CODE]
Console:
[CODE]Error: Unable to open /dev/sdb - unrecognised disk label.
A bug has been detected in GNU Parted.  Refer to the web site of parted http://www.gnu.org/software/parted/parted.html for more informations of what could be useful for bug submitting!  Please email a bug report to bug-parted@gnu.org containing at least the version (1.7.1) and the following message:  Assertion (disk != NULL) at ../../libparted/disk.c:1319 in function ped_disk_next_partition() failed.
```

**parted when trying print:**
```
Error: Unable to open /dev/sdb - unrecognised disk label.
```

The USB Stick could also be physically damaged, the people I gave it to handled it very rudely.

---

### Post by kidders on 2007-12-19
[SIZE=1]**Edit:** In light of a recent forum announcement regarding dangerous commands, I thought I should preface this post with a quick note:
[/SIZE]
[CENTER][B][COLOR=Red]The command (sudo dd...) I suggested mrc_001 should use is highly dangerous,
and can cause serious, irreversible damage if misapplied.[/COLOR][/B]
[/CENTER]
 
> **mrc_001 said:**
> the stick is completely empty, no partition table, no partitionOSX makes it awkward to do that ... incompatible or corrupt partition data may not be as "gone" as you think. You see, there is an important distinction between *deleting* and *erasing* a partition table.

Anyhow, I would suggest manually erasing any data that may be sitting where partition information normally would, and trying a more reliable partitioner (eg fdisk, cfdisk, etc.) to reconfigure your disk. One or other measure will hopefully fix your problems, whether they are due to the presence of confusing partition table data, or glitches in the partitioners you're using.

Wiping the first few megabytes of your disk should be more than enough to convince disk partitioners there's nothing on it. Something along the lines of the following should do the trick...```
sudo dd if=/dev/zero of=/dev/sda bs=1024k count=10
```Be _very careful_ to substitute the correct /dev path for "/dev/sda" though ... there's no way to undo the damage writing 10 megs of zeros onto the wrong disk would cause!

Personally, my favourite partitioner is cfdisk. It's lightweight (no GUI), but much friendlier than many other CLI-based ones. After you run it, you might want to run **sudo partprobe**, or unplug & re-attach your disk, to make sure Ubuntu re-scans the new partition table.

---

