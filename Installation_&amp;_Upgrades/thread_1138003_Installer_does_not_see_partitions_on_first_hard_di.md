---
title: "Installer does not see partitions on first hard disk"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by pjeeanah on 2009-04-26
As suggested in thread [http://ubuntuforums.org/showthread.php?t=1134856](http://ubuntuforums.org/showthread.php?t=1134856), I am starting a new thread.

I have two hard disks on my machine. I want to install jaunty on my first hard disk. 

The installer from the alternate CD does not show the partitions on my first hard disk. It just shows one whole /dev/sda with no partitions.

My second hard disk /dev/sdb shows the partitions ok. As suggested by meierfra. here is the output of fdisk -lu

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x020f020f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    48821534    24410736   83  Linux
/dev/sda2        48821535   310070564   130624515    5  Extended
/dev/sda3   *   185197320   236396474    25599577+   7  HPFS/NTFS
/dev/sda5        48821598    50781464      979933+  82  Linux swap / Solaris
/dev/sda6        50781528    81497744    15358108+  83  Linux
/dev/sda7        81497808   132696899    25599546   83  Linux
/dev/sda8       132696963   185197319    26250178+   e  W95 FAT16 (LBA)
/dev/sda9       236396538   310070564    36837013+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9da480c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   153597464    76798701    7  HPFS/NTFS
/dev/sdb2       153597465   173132504     9767520   83  Linux
/dev/sdb3       173132505   264943979    45905737+   5  Extended
/dev/sdb5       173132568   202435064    14651248+  83  Linux
/dev/sdb6       202435128   231737624    14651248+  83  Linux
/dev/sdb7       231737688   235641419     1951866   82  Linux swap / Solaris
/dev/sdb8       235641483   264943979    14651248+  83  Linux
```

The ouput of sfdisk -d is 

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 48821472, Id=83
/dev/sda2 : start= 48821535, size=261249030, Id= 5
/dev/sda3 : start=185197320, size= 51199155, Id= 7, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 48821598, size=  1959867, Id=82
/dev/sda6 : start= 50781528, size= 30716217, Id=83
/dev/sda7 : start= 81497808, size= 51199092, Id=83
/dev/sda8 : start=132696963, size= 52500357, Id= e
/dev/sda9 : start=236396538, size= 73674027, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=153597402, Id= 7, bootable
/dev/sdb2 : start=153597465, size= 19535040, Id=83
/dev/sdb3 : start=173132505, size= 91811475, Id= 5
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=173132568, size= 29302497, Id=83
/dev/sdb6 : start=202435128, size= 29302497, Id=83
/dev/sdb7 : start=231737688, size=  3903732, Id=82
/dev/sdb8 : start=235641483, size= 29302497, Id=83

```

How to make the installer see partition in /dev/sda?

Any help would be welcome.

---

### Post by meierfra. on 2009-04-26
The problem is that the primary partition /dev/sda3 sits inside the extended partition /dev/sda2.

To fix the partition table, boot from the LiveCD, download the attached file "PT.txt" to your Desktop and open a terminal. Then


```
sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
```

Just as a precaution, post the output of that commmand and copy the file OldPT.save to a save place outside your hard drive (Flashdrive, online storage, email account,...)

---

### Post by pjeeanah on 2009-04-26
Thanks  a lot. I am going to try it.

---

### Post by pjeeanah on 2009-04-26
I tried the command, here the outputs of fdisk -lu
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x020f020f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    48821534    24410736   83  Linux
/dev/sda2        48821535   185197319    68187892+   5  Extended
/dev/sda3   *   185197320   236396474    25599577+   7  HPFS/NTFS
/dev/sda4       236396538   310070564    36837013+   7  HPFS/NTFS
/dev/sda5        48821598    50781464      979933+  82  Linux swap / Solaris
/dev/sda6        50781528    81497744    15358108+  83  Linux
/dev/sda7        81497808   132696899    25599546   83  Linux
/dev/sda8       132696963   185197319    26250178+   e  W95 FAT16 (LBA)
```

The output of sfdisk -d is

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 48821472, Id=83
/dev/sda2 : start= 48821535, size=136375785, Id= 5
/dev/sda3 : start=185197320, size= 51199155, Id= 7, bootable
/dev/sda4 : start=236396538, size= 73674027, Id= 7
/dev/sda5 : start= 48821598, size=  1959867, Id=82
/dev/sda6 : start= 50781528, size= 30716217, Id=83
/dev/sda7 : start= 81497808, size= 51199092, Id=83
/dev/sda8 : start=132696963, size= 52500357, Id= e


```

The installer now sees the partitions in /dev/sda.

I have one problem. The free space in sda is marked unusable. I can delete /dev/sda4. Then the partioner can create a primary partition which
I don't want.

I want to create create a logical partition of about 20G and leave the rest free so I add other OSes. Can this be done?

Can I also delete partition /dev/sd8 which seems to contain nothing?

Thanks a lot folks.

---

### Post by meierfra. on 2009-04-26
> I want to create create a logical partition of about 20G and leave the rest free so I add other OSes. Can this be done?

Your primary partition /dev/sda3 is between the extended partition /dev/sda2 and the unallocated space.

To   create a new logical partition  partitions, you have to use gparted to move   /dev/sda4 and   /dev/sda3 to the end  of the hard drive, so that the unallocated space is next to /dev/sda2. Then you can add the unallocated space  to /dev/sda2.

Sometimes moving the start point of a Windows partition makes Windows unbootable, but that can be fixed.


> Can I also delete partition /dev/sd8 which seems to contain nothing?
Sure. Just make sure it really does not contain anything.

Backup any valuable data before doing any partitioning.

---

### Post by pjeeanah on 2009-04-26
I have copied the /dev/sda3 partition to /dev/sda8 using the gparted live cd. My windows boots from this new partition using grub. Now I plan to delete /dev/sda3. I think I will then have continuos free space.

Thank you for your help.

---

### Post by meierfra. on 2009-04-26
>  My windows boots from this new partition using grub.

You might actually still be booting the Windows on /dev/sda3.  If you aren't able to boot Windows after you deleted /dev/sda3, let me know and I can help you make /dev/sda8 bootable.

---

### Post by groova on 2009-04-26
Hi meierfra.

I am having the same problems (oulined [here]("http://ubuntuforums.org/showthread.php?t=1138158"))

These are my fdisk-results:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bab9bab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        6197    29294527+  83  Linux
/dev/sda3            6198       24321   145581030    5  Extended
/dev/sda4           23572       24321     6024343+  82  Linux swap / Solaris
/dev/sda5            6198       23571   139556592   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb51093e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      101587    51199816+   7  HPFS/NTFS
/dev/sdb2          101588      484518   192997224    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 40965687, Id= 7, bootable
/dev/sda2 : start= 40965750, size= 58589055, Id=83
/dev/sda3 : start= 99554805, size=291162060, Id= 5
/dev/sda4 : start=378668178, size= 12048687, Id=82
/dev/sda5 : start= 99554931, size=279113184, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=102399633, Id= 7
/dev/sdb2 : start=102399696, size=385994448, Id= 7
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

```

I downloaded your PT-files, but I don't quite get what you are doing in there #-o (yes, I am a windows-convert... ), so any chance you could help? Thanks.

---

### Post by meierfra. on 2009-04-26
**groova:**  Could you start a new thread with your problem? Trying to work two cases in one thread can be very confusing. Just send me a PM with a  link to  your new thread.

---

### Post by pjeeanah on 2009-04-26
Youre right! I am booting the same windows although I said grub to boot from /dev/sda8. It seems weird.

How to resove the problem? Better be safe than sorry. I have not yet deleted /dev/sda3.

---

### Post by meierfra. on 2009-04-26
> It seems weird.

The boot sector of a windows partition contains information where to look for further boot codes. Since you  copied the partition, sda8 has the same boot sector as sda3.   So the sda8 boot sector actually points back to the sda3 partition.

To fix your problem:

**Step1: ** Fix the boot sector of  sda8:

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select your new windows partition (/dev/sda8 ) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk,

** Step 2** Edit boot.ini

```
sudo  mount /dev/sda8 /mnt
sudo nano /mnt/boot.ini
```

Change both occurrences of 

partition(2)  

to

partition(7)


Follow the instructions on the bottom of the screen to save the file.
The "7" assumes that you did not delete /dev/sda3.
After you repartitioned the drive, you might have to change that number. Windows counts the same way as Linux, but it does not count extended partitions.  So /dev/sda8 turns into partition(7). But windows also doesn't count empty partitions in the partition table. So if  you delete /dev/sda3 without creating a new primary partition,  the "7" needs to be changed to "6"

---

### Post by pjeeanah on 2009-04-28
As usual you were very helpful meierfra. 

I deleted the /dev/sda3 and /dev/sda4 partitions. After using testdisk, I was able to boot windows.

But now I have a windows problem - I cannot log in. The Os starts fine but if I try to log in, it immediately logs me off.

May be drive letters have changed. I am going to use the savepart program to reset the drive letter in the registry. Will let you know then.

---

