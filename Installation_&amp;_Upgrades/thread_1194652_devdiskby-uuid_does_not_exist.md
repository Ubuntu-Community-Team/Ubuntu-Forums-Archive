---
title: "/dev/disk/by-uuid/ does not exist"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by aequasi on 2009-06-22
Hey guys, kinda new to linux, i have someone here helping me, but weve gone over forums over this topic and nothing we've read has fixed this.
 
Im runninga Gateway 955 dual xeon server and im getting this error on Ubuntu 9.04 
uname gave me this
 
ubuntu 2.6.28-11 generic #42-Ubuntu
i686
 
```

Boot from (hd0,0) ext3     4868f33b-f08d-4098-95fb-517586fb4e04
Starting up...
Gave up waitingfor root device. Common problems:
 - Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
   - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4868f33b-f08d-4098-95fb-517586fb4e04 does not exist.Dropping to a shell
```
 
then it displays the shell. 
 
Any help would be greatly appreciated :). Thanks in advance
 
 
im working ongetting my fstab right now
and here it is 
```

 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4868f33b-f08d-4098-95fb-517586fb4e04 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5a5a1bab-fa92-4587-9ad0-d07bfb6f1cb0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

 

```fdisk.out is here 
 
```

 

Disk /dev/sda: 36.7 GB, 36703934464 bytes
255 heads, 63 sectors/track, 4462 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x055e0dfe
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4273    34322841   83  Linux
/dev/sda2            4274        4462     1518142+   5  Extended
/dev/sda5            4274        4462     1518111   82  Linux swap / Solaris

 

```

---

### Post by nfox on 2009-07-11
I've had that happen to me twice now with Karmic and Grub2. This thread is marked solved and should fix it for you:

[http://ubuntuforums.org/showthread.php?t=813090]("http://ubuntuforums.org/showthread.php?t=813090")

---

