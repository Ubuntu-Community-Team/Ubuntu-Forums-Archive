---
title: "NTFS partition table messed up."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Canislupus on 2009-04-26
I've been following meierfra's solutions to several very similar problems.

My first SATA drive (1tb) is the problem.  It started as Win 7 repairing after I upgraded Ubuntu to 9.04.  Win 7 messed up the extended partition.

Anyway, I fixed the problem with testdisk, but I still have a problem with my partition sizes.

Meierfra, or someone similarly talented, can you see what this partition table needs?  

```

brent@brent-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0dc30dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   147460623    73730280+   7  HPFS/NTFS
/dev/sda2       147462144   147871743      204800    7  HPFS/NTFS
/dev/sda3       147871744   233199615    42663936    7  HPFS/NTFS
/dev/sda4       233215605  1953536129   860160262+   f  W95 Ext'd (LBA)
/dev/sda5       233215668   437996159   102390246    7  HPFS/NTFS
/dev/sda6       438003712  1052401663   307198976    7  HPFS/NTFS
/dev/sda7      1052403712  1953521663   450558976    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdcd0dcd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      787184      393561   83  Linux
/dev/sdb2          787185    31503464    15358140   83  Linux
/dev/sdb3        95249385   390716864   147733740    5  Extended
/dev/sdb4        31503465    95249384    31872960   83  Linux
/dev/sdb5        95249448   259578269    82164411   83  Linux
/dev/sdb6       387793098   390716864     1461883+  82  Linux swap / Solaris
/dev/sdb7       259578333   307018214    23719941   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4476f19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    81920159    40960048+   7  HPFS/NTFS


brent@brent-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=147460561, Id= 7, bootable
/dev/sda2 : start=147462144, size=   409600, Id= 7
/dev/sda3 : start=147871744, size= 85327872, Id= 7
/dev/sda4 : start=233215605, size=1720320525, Id= f
/dev/sda5 : start=233215668, size=204780492, Id= 7
/dev/sda6 : start=438003712, size=614397952, Id= 7
/dev/sda7 : start=1052403712, size=901117952, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=   787122, Id=83, bootable
/dev/sdb2 : start=   787185, size= 30716280, Id=83
/dev/sdb3 : start= 95249385, size=295467480, Id= 5
/dev/sdb4 : start= 31503465, size= 63745920, Id=83
/dev/sdb5 : start= 95249448, size=164328822, Id=83
/dev/sdb6 : start=387793098, size=  2923767, Id=82
/dev/sdb7 : start=259578333, size= 47439882, Id=83
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size= 81920097, Id= 7, bootable
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdd
unit: sectors


```

sda is the drive that I'm having the problem with.  It's bad enough that gparted refuses to try to read it (unallocated). But I can mount it, and all the data seems fine.   I noticed that sda7 ends outside the disk.  Parted just gives me a "partition cannot be outside disk" error or something to that effect.

Got another one of those handy-dandy text files? (TYIA)

---

### Post by meierfra. on 2009-04-26
You might be able to solve your problem with testdisk:

```
sudo testdisk /dev/sda
``` choose

"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" (to search for partitions created by vista)
Press "Enter" to continue,
"Extd Part"

This should shrink your extended partition has much as possible.  If this did not solve your problem, let me know and I show you how to rewrite the partition table with sfdisk.

---

### Post by Canislupus on 2009-04-26
I just tried that again. Just the way you requested this time. I wrote the discovered layout to disk, and rebooted. /sda2 is my Vista boot partition, so I made it active.

It seems it's still not working.   Incidentally, when I run testdisk on this drive, it doesn't ask me if I want to search for partitions created by Vista. It does ask when I run it on /dev/sdb (all Ext3 partitions).

Parted is still giving me this error:

```
(parted) check sda                                                        
Error: Can't have a partition outside the disk!                           
(parted) select /dev/sda
Using /dev/sda
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted)        
```                              

Also, I've noticed this:

```
brent@brent-desktop:~$ sudo fdisk /dev/sda -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, [COLOR="Red"]**121601**[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dc30dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9179    73730280+   7  HPFS/NTFS
/dev/sda2   *        9180        9205      204800    7  HPFS/NTFS
/dev/sda3            9205       14517    42663936    7  HPFS/NTFS
/dev/sda4           14518      [COLOR="Red"]**121602**[/COLOR]   860160262+   f  W95 Ext'd (LBA)
/dev/sda5           14518       27264   102390246    7  HPFS/NTFS
/dev/sda6           27265       65509   307198976    7  HPFS/NTFS
/dev/sda7           65510      [COLOR="Red"]**121602**[/COLOR]   450558976    7  HPFS/NTFS
brent@brent-desktop:~$ 
```

Is that the problem then?  It ends outside the disk, right? Or is it the fact that **testdisk** is set to stop on cylinder boundries? (the default behavior, I believe)

For the sake of giving you the most recent data, here are the current "fdisk -lu" and "sfdisk -d":

```
brent@brent-desktop:~$ sudo fdisk /dev/sda -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0dc30dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   147460623    73730280+   7  HPFS/NTFS
/dev/sda2   *   147462144   147871743      204800    7  HPFS/NTFS
/dev/sda3       147871744   233199615    42663936    7  HPFS/NTFS
/dev/sda4       233215605  1953536129   860160262+   f  W95 Ext'd (LBA)
/dev/sda5       233215668   437996159   102390246    7  HPFS/NTFS
/dev/sda6       438003712  1052401663   307198976    7  HPFS/NTFS
/dev/sda7      1052403712  1953521663   450558976    7  HPFS/NTFS
brent@brent-desktop:~$ sudo sfdisk /dev/sda -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=147460561, Id= 7
/dev/sda2 : start=147462144, size=   409600, Id= 7, bootable
/dev/sda3 : start=147871744, size= 85327872, Id= 7
/dev/sda4 : start=233215605, size=1720320525, Id= f
/dev/sda5 : start=233215668, size=204780492, Id= 7
/dev/sda6 : start=438003712, size=614397952, Id= 7
/dev/sda7 : start=1052403712, size=901117952, Id= 7
```

I can't thank you enough.  I'd attempt to manually edit it myself, but I don't have enough confidence in my ability to get it right.

---

### Post by meierfra. on 2009-04-26
> Is that the problem then? It ends outside the disk, right? Or is it the fact that testdisk is set to stop on cylinder boundries? (the default behavior, I believe)

Yes, Yes and Yes.  Your hard drive has somewhere between 121601 and 121692 cylinders. testdisk rounds that up to 12692 and  extended partition ends outside the hard drive.  That should not really matter, since nobody ever looks at the endpoint of an extended partition. But gparted is so picky about partition tables that it declares the partition table to be invalid and shows the whole drive as unallocated.


To fix the partition table, download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via

```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```

Post the output of that commmand.
Just as a precaution, copy the file OldPT.save to a save place outside your hard drive (Flashdrive, online storage,email account, ...)

---

### Post by Canislupus on 2009-04-26
meierfra. You rock! :guitar:

I CAN'T THANK YOU ENOUGH!

Here's the result:

```
brent@brent-desktop:~$ sudo fdisk /dev/sda -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dc30dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9179    73730280+   7  HPFS/NTFS
/dev/sda2   *        9180        9205      204800    7  HPFS/NTFS
/dev/sda3            9205       14517    42663936    7  HPFS/NTFS
/dev/sda4           14518      121602   860153029+   f  W95 Ext'd (LBA)
/dev/sda5           14518       27264   102390246    7  HPFS/NTFS
/dev/sda6           27265       65509   307198976    7  HPFS/NTFS
/dev/sda7           65510      121602   450558976    7  HPFS/NTFS
brent@brent-desktop:~$ sudo fdisk /dev/sda -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0dc30dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   147460623    73730280+   7  HPFS/NTFS
/dev/sda2   *   147462144   147871743      204800    7  HPFS/NTFS
/dev/sda3       147871744   233199615    42663936    7  HPFS/NTFS
/dev/sda4       233215605  1953521663   860153029+   f  W95 Ext'd (LBA)
/dev/sda5       233215668   437996159   102390246    7  HPFS/NTFS
/dev/sda6       438003712  1052401663   307198976    7  HPFS/NTFS
/dev/sda7      1052403712  1953521663   450558976    7  HPFS/NTFS
brent@brent-desktop:~$ sudo sfdisk /dev/sda -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=147460561, Id= 7
/dev/sda2 : start=147462144, size=   409600, Id= 7, bootable
/dev/sda3 : start=147871744, size= 85327872, Id= 7
/dev/sda4 : start=233215605, size=1720306059, Id= f
/dev/sda5 : start=233215668, size=204780492, Id= 7
/dev/sda6 : start=438003712, size=614397952, Id= 7
/dev/sda7 : start=1052403712, size=901117952, Id= 7
brent@brent-desktop:~$ sudo parted /dev/sda print
Model: ATA ST31000340AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  75.5GB  75.5GB  primary   ntfs              
 2      75.5GB  75.7GB  210MB   primary   ntfs         boot 
 3      75.7GB  119GB   43.7GB  primary   ntfs              
 4      119GB   1000GB  881GB   extended               lba  
 5      119GB   224GB   105GB   logical   ntfs              
 6      224GB   539GB   315GB   logical   ntfs              
 7      539GB   1000GB  461GB   logical   ntfs              

```

That works fine.  Data is readable and all.  Now I wonder what Win7 will do to that when I have it replace the bootloader?

I can't seem to decide what the best way to triple boot is. I'm not too wild about Vista/Win7's bootloader.  I'm thinking about installing Grub4DOS on /dev/sda1 and chainloading win7.

Guess I'll open another thread and see if I can get some input.

oh btw....

sfdisk -l  'Gives me an odd message for my /dev/sdc drive.

```
Disk /dev/sdc: 9729 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/240/63 (instead of 9729/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *        63  81920159   81920097   7  HPFS/NTFS
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty
```

Is that anything I should worry about?

---

### Post by meierfra. on 2009-04-26
> That works fine. Data is readable and all. 
Great.

> sfdisk -l 'Gives me an odd message for my /dev/sdc drive.
Warning: The partition table looks like it was made
  for C/H/S=*/240/63 (instead of 9729/255/63).
For this listing I'll assume that geometry.

Is that anything I should worry about? 

No. The partition table looks just fine.

> 
 I can't seem to decide what the best way to triple boot is. I'm not too wild about Vista/Win7's bootloader. I'm thinking about installing Grub4DOS on /dev/sda1 and chainloading win7.


Grub4Dos is a very nice boot loader and you should be able to boot all your OS's with Grub4Dos.
But keep in mind that the actual booting of Win 7 will be done by the Win 7 boot loader. So if you are not able to boot Win 7 with the Win 7 boot loader, Grub4Dos won't be able to boot it either.


> It started as Win 7 repairing after I upgraded Ubuntu to 9.04. Win 7 messed up the extended partition.

Now I wonder what Win7 will do to that when I have it replace the bootloader?


Upgrading to 9.04 should not have affected  Win 7. Did you resize the Win 7 partition?   
What problems did you have?  Any error messages? How did you try to repair it? 

I'm pretty sure one can repair the Win 7 boot loader without messing up your partitions again.

---

