---
title: "Adding windows 2008 entry to grub"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by westerdaled on 2009-03-05
Hi there

Ubuntu 8.10 is the default O/S on my 750Gb hard disk. I would like to install windows 2008 on either an extended or primary partition in the unused 250Gb at the end this disk


As a first attempt I have booted from the live CD and with the partition manager I have created a 250GB NTFS disk in an extended partition. now 
 

```
$ sudo fdisk -l
``` displays

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60807   488432196   83  Linux
/dev/sda2           60808       61305     4000185   82  Linux swap / Solaris
/dev/sda3           61306       91201   240139620    5  Extended
/dev/sda5           61306       91201   240139588+   7  HPFS/NTFS

Now, I need edit my grub menu

```
sudo gedit /boot/grub/menu.lst
```

I tried this an got an error 12....oh well
> 
title		Windows 2008
root		(hd0,4)
makeactive
chainloader	+1


A quick google search and came up with this entry in grub which gives an error 13

> title		Windows 2008
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,0)
makeactive
chainloader	+1

I guess I need to know if I am on the right lines or do I need to make the NTFS partition a primary partition. I am assuming I can install  (from dvd) and boot into windows in a partition at the end of my hard disk

Cheers

Daniel

---

### Post by ajgreeny on 2009-03-05
I think it is very difficult to get windows to boot from an extended partition, though apparently not impossible.  I suggest you repartition and make the windows partition a primary one.  You should have no problem from then.

---

### Post by westerdaled on 2009-03-05
Thanks for the info. As long I can dual boot the proposed primary windows partition with my beloved Ubuntu 8.10 then I will be happy. Incidently, If I need a plan B then I noticed in this thread[http://ubuntuforums.org/showthread.php?t=1086319]("http://ubuntuforums.org/showthread.php?t=1086319")
I could do some interesting things with EasyBCD..I but hopefully I I won't need to go down this path.:D

Thanks again

---

### Post by westerdaled on 2009-03-09
I have now repartition the extended partition as a NTFS primary partition.

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60807   488432196   83  Linux
/dev/sda2           60808       61305     4000185   82  Linux swap / Solaris
/dev/sda3           61306       91201   240139620    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS


My grub item looks like this now
```
title		Windows 2008
root		(hd0,2)
#map (hd0,0) (hd0,2)
#map (hd0,2) (hd0,0)
# rootnoverify (hd0,0)
makeactive
chainloader	+1
```

On selection I now get the error: 
> BOOTMRG Missing press any key to reboot
If this is valid  I guess I now want the bootloader to try to install from my win2008 dvd. How can I make this happen? Any help would be appreciated.


Daniel

---

