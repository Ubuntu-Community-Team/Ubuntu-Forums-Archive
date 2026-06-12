---
title: "partition table fixing."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by hammedhaaret on 2009-04-26
Hi.
I'm trying to install jaunty and have run into the problem that ubuntu can't recognize my partitions. It sees it all as unallocated space.

I know there are several threads about the same problem, ([http://ubuntuforums.org/showthread.php?t=1138158](http://ubuntuforums.org/showthread.php?t=1138158))
but I can't seem to understand what the solution is.
apparently my partition table needs fixing and I don't know how to do that.
I have tried TestDisk but that's a little over my head.


Here's output of fdisk -lu and sfdisk -d
```
omitting empty partition (5)

Disk /dev/sda: 80.0 Gb, 80026361856 byte
255 heads, 63 sectors/track, 9729 cylinders, i alt 156301488 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0xcc9bcc9b

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *          63    33382943    16691440+   7  HPFS/NTFS
Partition 1 slutter ikke på en cylindergrænse. *
/dev/sda2        33383070   156296384    61456657+   5  Udvidet
Partition 2 slutter ikke på en cylindergrænse. *
/dev/sda3       153308358   156296384     1494013+  82  Linux swap / Solaris
Partition 3 slutter ikke på en cylindergrænse. *
/dev/sda5        33383196    47841569     7229187   83  Linux
/dev/sda6        47841633   153308294    52733331   83  Linux
```

* Partition 1/2/3 doesn't end on cylinder border

```
# partitionstabel for /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 33382881, Id= 7, bootable
/dev/sda2 : start= 33383070, size=122913315, Id= 5
/dev/sda3 : start=153308358, size=  2988027, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 33383196, size= 14458374, Id=83
/dev/sda6 : start= 47841633, size=105466662, Id=83

```

any help is welcome

---

### Post by sgosnell on 2009-04-26
Boot from the install CD, choose to try without changing your system, and when you get the desktop, run the partition manager (gparted).  Delete all the partitions, add a new primary partition, and format it.  Then exit gparted, and try the install.

---

### Post by meierfra. on 2009-04-26
To fix your partition table, download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```


Just as a precaution, post the output of that command. Also  copy the file
OldPT.save to a save place outside your hard drive (Flashdrive, online
storage,email account,...)

---

### Post by hammedhaaret on 2009-04-27
Here is the output:
```
Disk /dev/sda: 9729 cylindre, 255 hoveder, 63 sektorer/spor
Gammel situation:
Enheder = cylindre á 8225280 byte, blokke á 1024 byte, tæller fra 0

   Enhed  Opst Start     Slut  #cyldr. #blokke   Id  System
/dev/sda1   *      0+   2077-   2078-  16691440+   7  HPFS/NTFS
		slut: (c,h,s) forventede (1023,254,63) fandt (1023,15,63)
/dev/sda2       2078    9728    7651   61456657+   5  Udvidet
		start: (c,h,s) forventede (1023,254,63) fandt (1023,2,1)
		slut: (c,h,s) forventede (1023,254,63) fandt (1023,14,63)
/dev/sda3       9543+   9728     186-   1494013+  82  Linux swap / Solaris
		start: (c,h,s) forventede (1023,254,63) fandt (1023,10,1)
		slut: (c,h,s) forventede (1023,254,63) fandt (1023,14,63)
/dev/sda4          0       -       0          0    0  Tom
/dev/sda5       2078+   2977     900-   7229187   83  Linux
		start: (c,h,s) forventede (1023,254,63) fandt (1023,4,1)
		slut: (c,h,s) forventede (1023,254,63) fandt (1023,13,63)
/dev/sda6       2978+   9542    6565-  52733331   83  Linux
		start: (c,h,s) forventede (1023,254,63) fandt (1023,15,1)
		slut: (c,h,s) forventede (1023,254,63) fandt (1023,8,63)
Ny situation:
Enheder = sektorer á 512 byte, tæller fra 0

   Enhed  Opstart Start       Slut  #sektorer Id  System
/dev/sda1   *        63  33382943   33382881   7  HPFS/NTFS
/dev/sda2      33383070 156296384  122913315   5  Udvidet
/dev/sda3             0         -          0   0  Tom
/dev/sda4             0         -          0   0  Tom
/dev/sda5      33383196  47841569   14458374  83  Linux
/dev/sda6      47841633 153308294  105466662  83  Linux
/dev/sda7     153308358 156296384    2988027  82  Linux swap / Solaris
Advarsel: partition 1 slutter ikke på en cylindergrænse
Skrivning af ny partitionstabel lykkedes

Genindlæser partitionstabel ...
BLKRRPART: Device or resource busy
Kommandoen for genindlæsning af partitionstabellen mislykkedes
Genstart dit system nu, før du formatterer med mkfs

Hvis du oprettede eller ændrede en DOS-partition, f.eks. /dev/xxx7, så brug
dd(1) til at nulstille de første 512 byte:
'dd if=/dev/zero of=/dev/xxx7 bs=512 count=1'  (se fdisk(8))
```


saving the OldPT.txt.

Any idea of what happened to the PT?

thanks a lot for the help.

---

### Post by meierfra. on 2009-04-27
The output looks fine. Before you reboot you should reinstall grub:

```
sudo grub
```

and at the "grub>" prompt

```
find /boot/grub/stage2
find /grub/stage2
```

One of these commands should return "(hd0,4)"  or "(hd0,5)"

```
root (hd0,4)  (use whatever you got from the find command)
setup
quit
```


Reboot, and you should be all set.


> Any idea of what happened to the PT?
Usually this happens if you use two different partitioning tools. Different partitioning tools  use slightly different rules for the partition table, and that can lead to confusion. Sometimes its enough to install Ubuntu and reinstall XP.

---

