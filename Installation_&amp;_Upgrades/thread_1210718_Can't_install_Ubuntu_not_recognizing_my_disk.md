---
title: "Can't install Ubuntu: not recognizing my disk"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by yang on 2009-07-11
I'd like to install Ubuntu alongside my existing XP install onto my HP Compaq nc6400, but the live CD doesn't seem to be cooperating with my NTFS partition.  I don't want to wipe out XP, so I need to resize the partition, but none of the tools seem to be working:

```

$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc39a9a07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sdb: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         502     4030432    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)

$ sudo mount -t ntfs /dev/sda1 /mnt/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

$ sudo ntfsresize -if /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sda1' as NTFS failed: Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).

```

I also tried specifying /dev/sda instead of /dev/sda1.  I also tried using GParted, but it just says I have a single partition (/dev/sda1) with an unknown filesystem.  Windows XP is working fine.

Thanks in advance for any help.

---

### Post by 1roxtar on 2009-07-11
Forget partitions! Install Ubuntu INSIDE Windows with Wubi.  On the live cd, just choose the option to "Install Inside Windows".  It works easier and you can uninstall it like any other Windows program if you wanted to.

---

### Post by PukingPenguin on 2009-07-11
Yeah, or forget Wubi and partition the disk like it should be. Before trying to partition the disk, use the windows defrag tool several times to defrag the ntfs partition. After that, if gparted won't work, post back with some specific errors, and someone will come up with an answer.

---

### Post by presence1960 on 2009-07-11
Wubi is meant to be used as a trial to see if you like Ubuntu this way you don't have to partition your existing setup. Even though wubi is supposed to be a trial to see if you like Ubuntu I realize some people for different reasons wind up using it permanently. If you read the wubi documentation you will see that wubi's performance will become degraded due to fragmentation of the windows file system. If you just want to try ubuntu then give wubi a whirl. if you want to keep Ubuntu you will have to eventually partition your hard disk.

Some things to look at in regards to your install problem:

1. did you do MD5SUM on the downloaded iso prior to burning it to disk?
   [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  
   then check against Ubuntu hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2. Burn image to disc at slowest possible speed...4x is perfect
3. Defrag windows at least once or twice prior to resizing its partition. If it is Vista use Vista's disk management utility to shrink Vista's partition and create space for Ubuntu.
4. Boot Live CD and use check cd for defects first. 
5. if you still have the same problem download the alternate text based installer. get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

P.S. here is a link for wubi to back up my words: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by merlinus on 2009-07-11
You might try running chkdsk c: /f from windows.

---

### Post by yang on 2009-07-12
1roxtar: I don't want to use Wubi, since I've been using Ubuntu as my main OS for several years.  Once I have Ubuntu running smoothly I intend to remove XP all together.

merlinus and PokingPenguin: I ran both chkdsk c: /f (scanning/fixing at reboot) and defrag, to no avail.

presence1960: (1) The md5sum verifies.  (2, 4) I didn't burn to a CD; I booted from USB.  Also I'm using XP not Vista.  (3) Defrag didn't do anything.  (5) Alternate install CD gives me the same thing.

---

### Post by merlinus on 2009-07-12
Just checking to be sure:

sudo mount -t ntfs /dev/sda1 /mnt/sda1

You did create the mountpoint first???

---

### Post by yang on 2009-07-12
merlinus: yeah (otherwise the error I pasted would have reported that first).

---

### Post by merlinus on 2009-07-12
OK.  Just wanted to be sure....

Have you tried gparted live to see if it will recognize sda1?  Also, I wonder if using a cd instead of usb would make any difference.

---

### Post by yang on 2009-07-12
Hey merlinus.  Yeap, as stated in my original post, GParted only sees /sdev/sda1 as having an unknown FS.

I did in fact also try with a GParted Live CD, but got the same results.

---

### Post by yang on 2009-07-12
Some more details: after running "mount -t ntfs -o errors=recover ...", dmesg shows:

```

NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
NTFS-fs error (device sda): read_ntfs_boot_sector(): Could not find a valid backup boot sector.
NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.

```

---

### Post by merlinus on 2009-07-12
Did you try force mounting it?

```
sudo mount -t ntfs /dev/sda1 /mnt/sda1 -o force
```

---

### Post by yang on 2009-07-13
Just tried that, and got the same results.

---

