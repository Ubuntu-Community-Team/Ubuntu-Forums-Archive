---
title: "[SOLVED] Partitions don't show up in GParted"
date: 2008-11-29
forum: General Help
---

### Post by raycosm on 2008-11-29
So a while back I deleted my partition table and GRUB, but restored them using testdisk (the process was in this thread [http://ubuntuforums.org/showthread.php?t=958364]("http://ubuntuforums.org/showthread.php?t=958364")). Everything was pretty usable, but I wanted to do a fresh upgrade to Interpid from Linux Mint Elyssa. Thing is, the partition editor in the installer doesn't list any partitions, and I don't want to wipe the whole disk considering I have my /home and Vista on it still.

sudo fdisk -l gives me
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020       14210   105956707+   7  HPFS/NTFS
/dev/sda3           14211       15091     7076632+  83  Linux
/dev/sda4           15092       19458    35077927+   f  W95 Ext'd (LBA)
/dev/sda5           15092       19329    34041703+  83  Linux
/dev/sda6           19330       19457     1028128+  82  Linux swap / Solaris
```

sda1 is an Acer recovery partition, sda2 is Vista. sda3 is Linux, sda4 is (I think that's what you call it) a logical partition containng sda5 which is /home and sda6 which is swap. None of these partitions show up in GParted on the installer, or GParted on my computer, it just says I have a whole unallocated hard drive.

---

### Post by jpeddicord on 2008-11-29
This may seem obvious: check to make sure that you have the right drive selected on the top-right of GParted. If fdisk can find your partitions properly, GParted shouldn't be having a problem afaik.

---

### Post by caljohnsmith on 2008-11-29
Still having problems with your partition table? Thought we had that solved, but maybe not. :) How about first posting the output of:
```
sudo parted /dev/sda print
```
And also, I think it would be good to run testdisk again and see if it complains about your partition table, because maybe something happened since the time when it was recovered:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by raycosm on 2008-11-29
sudo parted /dev/sda print

```
Error: Can't have a partition outside the disk!                           
Information: Don't forget to update /etc/fstab, if necessary.
```

It sounds like I need to update my fstab or something, which is probably an easy fix, but I have no idea how to do that.

A quick run of testdisk (without deeper searching) shows this.

```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Compaq Diagnostics       0   1  1  1018 254 63   16370172
 2 * HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
 3 P Linux                14210   0  1 15090 254 63   14153265
 4 E extended LBA         15091   0  1 19457 254 63   70155855
 5 L Linux                15091   1  1 19328 254 63   68083407
   X extended             19329   0  1 19456 254 63    2056320
 6 L Linux Swap           19329   1  1 19456 254 63    2056257







*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

That was without the deeper search though, I'm running that right now. Looks pretty normal, although I wouldn't know.

---

### Post by caljohnsmith on 2008-11-30
OK, I think I see why gparted/parted complains about your partition table:
> **raycosm said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, [COLOR="Red"]19457[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020       14210   105956707+   7  HPFS/NTFS
/dev/sda3           14211       15091     7076632+  83  Linux
/dev/sda4           15092       [COLOR="Red"]19458[/COLOR]    35077927+   f  W95 Ext'd (LBA)
/dev/sda5           15092       19329    34041703+  83  Linux
/dev/sda6           19330       19457     1028128+  82  Linux swap / Solaris
```
Notice that your HDD has a total of 19457 cylinders, yet the sda4 extended partition ends at 19458 cylinders; fortunately sda6 correctly ends at 19457 cylinders, so hopefully it won't be a big deal to fix the problem. I'm wondering if that was a problem with testdisk when you used it a month ago to recreate the partition table.

After you get the deep search results, please select each partition (except the swap partition) and press "P" to list the root directory of that partition; let me know which partitions correctly show their root directories. Also, please post:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by raycosm on 2008-11-30
Deeper search
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1018 254 63   16370172 [PQSERVICE]NTFS, 838
P HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
P Linux                14210   0  1 15090 254 63   14153265
D Linux                15091   1  1 19328 254 63   68083407
D Linux                15092   2  1 19330 254 63   68099409
D Linux Swap           19329   1  1 19456 254 63    2056257







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
```

I made it segfault somehow before I could push P, but I'm doing it over and have to wait another hour.

sudo fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086   12  Compaq diagnostics
/dev/sda2   *    16370235   228283649   105956707+   7  HPFS/NTFS
/dev/sda3       228283650   242436914     7076632+  83  Linux
/dev/sda4       242436915   312592769    35077927+   f  W95 Ext'd (LBA)
/dev/sda5       242436978   310520384    34041703+  83  Linux
/dev/sda6       310520448   312576704     1028128+  82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-11-30
> **raycosm said:**
> Deeper search
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] HPFS - NTFS              0   1  1  1018 254 63   16370172 [PQSERVICE]NTFS, 838
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
[COLOR="Red"]P[/COLOR] Linux                14210   0  1 15090 254 63   14153265
[COLOR="Red"]L[/COLOR] Linux                15091   1  1 19328 254 63   68083407
[COLOR="Red"]D[/COLOR] Linux                15092   2  1 19330 254 63   68099409
[COLOR="Red"]L[/COLOR] Linux Swap           19329   1  1 19456 254 63    2056257

```

I see you are using testdisk version 6.8, so please don't try the "P" function on any NTFS partitions, or unfortunately the program will crash like it did for you before. Anyway, I've marked each partition above with either "*", "P", "D", and "L" to represent what I believe is your correct partition table. I think it is quite clear since the only questionable partition is the third linux partition above which overlaps with the swap partition, so it can't be valid unless the swap partition is invalid. How about marking the partitions as I've shown above, press enter to continue, and then write the new partition table to the HDD. Then reboot, and please post the new output of:
```
sudo parted /dev/sda print
sudo fdisk -lu
```
So I can help you double check that everything looks OK.

---

### Post by raycosm on 2008-11-30
So I did another deep search because the first one segfaulted, for some reason there are now FOUR partitions listed as Linux and a Linux Swap partition.

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
P HPFS - NTFS              0   1  1  1018 254 63   16370172 [PQSERVICE]
* HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
P Linux                14210   0  1 15090 254 63   14153265
L Linux                15091   1  1 19328 254 63   68083407
D Linux                15092   2  1 19330 254 63   68099409
L Linux                15099   1  1 19336 254 63   68083407
L Linux Swap           19329   1  1 19456 254 63    2056257
```

I'm not quite sure what to do, and I'm still on this screen right now. I tried to follow the letters you gave me, but I didn't write anything and I am still at the screen.

---

### Post by caljohnsmith on 2008-11-30
> **raycosm said:**
> 
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] HPFS - NTFS              0   1  1  1018 254 63   16370172 [PQSERVICE]
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
[COLOR="Red"]P[/COLOR] Linux                14210   0  1 15090 254 63   14153265
[COLOR="Red"]L[/COLOR] Linux                15091   1  1 19328 254 63   68083407
[COLOR="Red"]D[/COLOR] Linux                15092   2  1 19330 254 63   68099409
[COLOR="Red"]D[/COLOR] Linux                15099   1  1 19336 254 63   68083407
[COLOR="Red"]L[/COLOR] Linux Swap           19329   1  1 19456 254 63    2056257
```


OK, that fourth linux partition must be invalid too if your swap partition is valid; but to make sure you have the correct linux partition, select the second linux partition above (starts at 15091 and ends at 19328 ), and press "P" to list its root directory. If that works, then I believe the above partition table should be correct. Make sure you are careful to mark each partition exactly as shown above (highlighted in red), then go ahead and write it to the HDD. Then reboot, and please post the commands I gave in my previous post; we can go from there.

---

### Post by raycosm on 2008-11-30
"sudo parted /dev/sda print" gives the same message as before
```
Error: Can't have a partition outside the disk!                           
Information: Don't forget to update /etc/fstab, if necessary.
```
"sudo fdisk -lu" looks the same too, except under "Id" /dev/sda1 has a 7 now instead of 12.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086    7  HPFS/NTFS
/dev/sda2   *    16370235   228283649   105956707+   7  HPFS/NTFS
/dev/sda3       228283650   242436914     7076632+  83  Linux
/dev/sda4       242436915   312592769    35077927+   f  W95 Ext'd (LBA)
/dev/sda5       242436978   310520384    34041703+  83  Linux
/dev/sda6       310520448   312576704     1028128+  82  Linux swap / Solaris
```

---

### Post by caljohnsmith on 2008-11-30
That's seems really strange that testdisk created an extended partition with an end point that goes beyond the boundary of your HDD; I don't think it should have done that because the end point of the last logical partition (the swap partition) is within the disk boundaries. 

How about doing the following:
```
sudo parted /dev/sda
```
At the parted prompt, do:
```
rm 4
mkpart extended 242436915s 312576704s
```
And please make sure to type those numbers in exactly right, or better to copy/paste them if you can. Then quit parted (just type "quit"), and again do:
```
sudo parted /dev/sda print 
```
And please post the output.

---

### Post by meierfra. on 2008-11-30
> rm 4
mkpart extended 242436915s 312576704s

"rm 4" is  going to give you an error messages since the home  and swap partitions are mounted.

But you should be able to solve your problem with testdisk.
At the screen with the  deeper search tab, you should also have  a "Extd Part" tab.  Select that tab and press "enter". Then you should be able to choose whether you want your extended partition to  be  as large or as small as possible. Choose it as small as possible. (Edit: the correct procedure is little different, see my next post) Hopefully that will take care of your problem.


> That's seems really strange that testdisk created an extended partition with an end point that goes beyond the boundary of your HDD;

tesdisk seems to think that the disk has 19458 cylinder: 

> Disk /dev/sda - 160 GB / 149 GiB - CHS [COLOR="Red"]19458 [/COLOR]255 63


But fdisk says:

> Disk /dev/sda: 160.0 GB, [COLOR="Blue"]160041885696[/COLOR] bytes
255 heads, 63 sectors/track, [COLOR="Red"]19457[/COLOR] cylinders
Units = cylinders of 16065 * 512 = [COLOR="Blue"]8225280[/COLOR] bytes

The total disk has   160041885696 bytes . Each cylinder has 8225280 bytes. So your disk has

160041885696/8225280= 19457.31...

cylinders.  That's not supposed to happen.

---

### Post by meierfra. on 2008-12-01
> Select that tab and press "enter". Then you should be able to choose whether you want your extended partition to be as large or as small as possible. Choose it as small as possible. Hopefully that will take care of your problem.

Correction (I just tried it out myself):  Select the "Extd tab" and press enter. That is enough to minimize the extended partition. (The end point of the extended partition should have changed). Choose "write" to save the new partition table and you should be all set.

---

### Post by raycosm on 2008-12-01
rm 4 gives the old "Error: Can't have a partition outside the disk!" even if I run it from a LiveCD with my harddrive unmounted.

I'm doing a deep search on testdisk right now, I couldn't find the "Extd Part" tab, is it after I do a deeper search? Maybe a screenshot would help.

These deeper searches take forever.

EDIT: For some reason the option isn't there, even when I try to use testdisk 6.10. The option is there on my other laptop using testdisk 6.9 and Intrepid.

---

### Post by meierfra. on 2008-12-01
You shoul have the  "extd tab" option already after the quick search.  You only get the option if the minimal size is not equal to the maximal size.  But in your case since the last partition ends before the extended partition, you really should get the "extd tab".  If you still don't have the "extd tab" after the deeper search, I suggested to use "sfdisk" to backup your partition table and then rewrite it.  To backup the partition table:

```
sudo sfdisk -d /dev/sda > PTold.txt
```
Post  the output of

```
cat PTold.txt
```

(You might also copy the file to flash drive, but posting it here should already be a good enough  backup)

Then 

```
sudo cp PTold.txt PTnew.txt
gksudo gedit PTnew.txt
```

Look for the line

/dev/sda4 start=242436915 size=70155855  Id=f 

and change it to

dev/sda4 start=242436915 size=70139790 Id=f


So only the size of the extended partition /dev/sda4 needs to be changed. Save the file.


Then

```
sudo sfdisk --force /dev/sda < PTnew.txt
```
This will write the new partition table to disk.

Type

 ```
sudo fdisk -lu 
```

The  extended partition should now end at the same place as the swap partition.

---

### Post by raycosm on 2008-12-01
The Extd Tab never did show up, so here goes.

PTold.txt
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 16370172, Id= 7
/dev/sda2 : start= 16370235, size=211913415, Id= 7, bootable
/dev/sda3 : start=228283650, size= 14153265, Id=83
/dev/sda4 : start=242436915, size= 70155855, Id= f
/dev/sda5 : start=242436978, size= 68083407, Id=83
/dev/sda6 : start=310520448, size=  2056257, Id=82

```

sudo fdisk -lu

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086    7  HPFS/NTFS
/dev/sda2   *    16370235   228283649   105956707+   7  HPFS/NTFS
/dev/sda3       228283650   242436914     7076632+  83  Linux
/dev/sda4       242436915   312576704    35069895    f  W95 Ext'd (LBA)
/dev/sda5       242436978   310520384    34041703+  83  Linux
/dev/sda6       310520448   312576704     1028128+  82  Linux swap / Solaris

```

Well look at that, no reboot was even needed.

[IMG]http://img440.imageshack.us/my.php?image=screenshotdevsdagpartedky6.png[/IMG]

Thank you very much, caljohmsmith and meierfra for your help. :popcorn:

---

