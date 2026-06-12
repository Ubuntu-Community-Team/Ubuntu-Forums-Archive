---
title: "ubuntu installer Doesn't read my partitions"
date: 2009-10-08
forum: Hardware
---

### Post by kebomix on 2009-10-08
hello , I have Toshiba satellite A300-29N 

Nautilus can read and open partitions without any problems 
but when i try to install ubuntu ( ubuntu installer Doesn't read my partitions )  even gparted read my hard disk as unallocated 
here is a screen-shot 
[http://img156.imageshack.us/img156/5143/screenshotlv.png](http://img156.imageshack.us/img156/5143/screenshotlv.png)

and here is the output of 
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
**Partition 1 does not end on cylinder boundary.**
/dev/sda2   *         192        9982    78643371    7  HPFS/NTFS
/dev/sda3           19628       20933    10490442+   7  HPFS/NTFS
/dev/sda4            9983       38913   232388257+   5  Extended
/dev/sda5            9983       14014    32387008+   7  HPFS/NTFS
/dev/sda6           14015       19627    45086391    7  HPFS/NTFS
/dev/sda7           20934       30724    78646176    7  HPFS/NTFS
/dev/sda8           30725       38913    65778111    7  HPFS/NTFS

Partition table entries are not in disk order
```

any solution because i can't install ubuntu or any other Linux Disto. :confused::confused::confused:

---

### Post by louieb on 2009-10-08
Are you dual booting 2 windows OS (XP and Win7 maybe) your partition table looks like the work of the windows installer.  

Anyway the disk has a non-standard partition table - there is a primary partition inside an extended partition. Gparted and parted (used by the installer) detects that shows a blank drive. 

I've rearranged the listing to start order.
```

/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192        9982    78643371    7  HPFS/NTFS
/dev/sda4            [COLOR=Red]9983       38913[/COLOR]   232388257+   5  [COLOR=Red]Extended[/COLOR]
/dev/sda5            9983       14014    32387008+   7  HPFS/NTFS
/dev/sda6           14015       19627    45086391    7  HPFS/NTFS
/dev/sda3           [COLOR=Red]19628       20933[/COLOR]    10490442+   7  [COLOR=Red]HPFS/NTFS[/COLOR]
/dev/sda7           20934       30724    78646176    7  HPFS/NTFS
/dev/sda8           30725       38913    65778111    7  HPFS/NTFS


```

Don't know of any graphical tools that can change sda3 to a logical partition. **sfdisk ** can but its not a good tool for the inexperienced. 

Do you know what is on sda3? Because it has logical partition on both sides of it -  May be the easiest way to deal with it is to use testdisk and delete it.   Then Gparted will see the disk and you can use the space to make a logical partition for a Linux install and a 2nd logical partitionfor linux swap.

---

