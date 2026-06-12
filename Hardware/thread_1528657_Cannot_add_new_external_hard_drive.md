---
title: "Cannot add new external hard drive"
date: 2010-07-11
forum: Hardware
---

### Post by silentrebel on 2010-07-11
I have a server running Ubuntu 10.04.

It currently has one 500Gb external hard drive connected to it and it works fine.  When I connect a second external hard drive, the machine won't boot...  It gets stuck with the following message:

> 
mount: you must specify the filesystem type
mountall: mount /media/boundscrolls [2055] terminated with status 32
mountall: filesystem could not be mounted /media/boundscrolls


(By the way, boundscrolls is the old external; chinguetti is the new one.)  I find it strange that adding a new hard drive would cause so much trouble for the one that used to work...

Here is the output of fdisk -l before adding the second hard drive:
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda933ddb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15728640   27  Unknown
/dev/sda2            1959        1972      102400    7  HPFS/NTFS
/dev/sda3            1972       20208   146484375    7  HPFS/NTFS
/dev/sda4           20208       91202   570256385    5  Extended
/dev/sda5           20208       89062   553065472   83  Linux
/dev/sda6           89062       91202    17189888   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

Here is my fstab before adding the new external:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f50561d6-05e0-4248-a573-2b49cc4e3374 /               ext4    errors=remount-ro 0       0
# swap was on /dev/sda6 during installation
UUID=d5a21f93-bebf-4ffc-8519-ca8f52f1e47c none            swap    sw              0       0
/dev/sdb	/media/boundscrolls	auto	defaults	0	0

```

I added this line to my fstab for the new hard drive because fdisk -l indicated that this is what I should be doing (sorry, I do not have that output with me right now...)

```
/dev/sdh1        /media/chinguetti     ext3    defaults        0       0
```

In case it is of any importance, the new external only has one partition...

Thanks very much your help,
Nuagerebelle

---

### Post by IcarusR on 2010-07-11
> mount: you must specify the filesystem type

Suggest you do as this says & put a filesystem type for the drive in fstab, then try again.

Will it boot if neither external drives connected ? & with just original connected ?

Have you tried removing both drives from fstab, reboot without them connected, then connect & letting ubuntu automount them ??

> /dev/sdh1        /media/chinguetti     ext3    defaults        0       0

Do you actually have 8 drives on this machine, is sdh correct ?

---

### Post by silentrebel on 2010-07-11
I've already tried a million combinations to try and make it work (some of the combinations are included in your suggestions, IcarusR), but I'll try all of your suggestions later today.

In the meantime, regarding this...
> **IcarusR said:**
> Do you actually have 8 drives on this machine, is sdh correct ?

Aside from the new external, I only have two hard drives plugged into this computer.  However, it definitely finds this hard drive in sdh1, I can't tell you why.  In fact, I tried formating and mounting sdc for a very long time without success before I noticed that the new hard drive was hiding in this unlikely place.  Does anyone know why?

---

### Post by silentrebel on 2010-07-11
After a good night's sleep, I finally figured out what I had to do to fix the situation.  

I could only boot with the original configuration (with the first external hard drive connected and configured in fstab (no new second external), as shown above).  Naturally, Ubuntu would assign this volume to /dev/sdb.  After boot, when I connected the new second hard drive, Ubuntu would assign it to /dev/sdh1 (does anyone know why?).  

However, when I booted with both drives connected and configured in fstab (as shown in the original post), I would get error messages concerning the first hard drive which had always worked without a problem.  Thus, one could assume (and I might be wrong in saying this) that the sd* addresses that I saw after hot-connecting the second hard drive were not the same as those assigned at startup when both hard drives were connected.  As a result, my fstab entries would be invalid.

So, to help fstab not get confused about which hard drive to mount where, I used UUIDs.

To find out the UUID of your hard drive, connect it and enter this into the terminal:
```
sudo ls -l /dev/disk/by-uuid 
```
This will show which /dev/sd* correspond to which UUID.

You can then configure your fstab a little like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f50561d6-05e0-4248-a573-2b49cc4e3374 /               ext4    errors=remount-ro 0       0
# swap was on /dev/sda6 during installation
UUID=d5a21f93-bebf-4ffc-8519-ca8f52f1e47c none            swap    sw              0       0
UUID=8e4ef937-deb6-4e41-984b-cfcd0d9ebb02	/media/boundscrolls	auto	defaults	0	0

UUID=3b09f79f-4d5f-4268-9353-d02ab198770a      /media/chinguetti     ext3    defaults        0       0
```

Best of luck to all those who encounter this potentially frustrating problem...
Nuagerebelle

---

