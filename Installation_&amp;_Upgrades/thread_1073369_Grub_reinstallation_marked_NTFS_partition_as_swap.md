---
title: "Grub reinstallation marked NTFS partition as swap"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by shtephutz on 2009-02-18
Hi.
This is my first post..so if I do something wrong, pls tell me.
Thanks.
My problem is that i have a notebook with 2 OS's installed, of course that one of them is Ubuntu 8.04...Yesterday I wanted to try another OS along with Ubuntu, so I installed it and verry fast got rid of it....anyways..To boot any OS I had to reinstall grub from the liveCD as always did , but now this occured:my HDD looked like this before any of above ops':
200 mb NTFS_primary
17000 mb NTFS_primary
50000 mb NTFS_logical
7000 mb ext3_Ubuntu's
392 mb swap_Ubuntu's;
and now it looks like this:
200 mb NTFS_primary
17000 mb NTFS_primary
7000 mb ext3_Ubuntu's
50000 mb Swap
392 mb unallocated.
The problem is the 50000 mb partitionon wich I had many useful things, and consists in the following : not accessible from any os and I'm unable to recover my files.
Is there any way to repair this?
Thanks in advance!

---

### Post by caljohnsmith on 2009-02-18
How about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by shtephutz on 2009-02-18
root@MSI:/home/shtephutz# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3640363f

  Sorry for the delay...I just got home from work.
Thanks for the understanding
The outputs are :
--for fdisk -lu:
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          411648    37495709    18542031    7  HPFS/NTFS
/dev/sda3        37495710   156296384    59400337+   f  W95 Ext'd (LBA)
/dev/sda5        37495836    53078822     7791493+  83  Linux
/dev/sda6        53078823   155493134    51207156    7  HPFS/NTFS

Disk /dev/sdb: 8199 MB, 8199864320 bytes
233 heads, 4 sectors/track, 17183 cylinders, total 16015360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22452244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192    16015359     8003584    7  HPFS/NTFS
--and for sfdisk -d:
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   409600, Id= 7, bootable
/dev/sda2 : start=   411648, size= 37084062, Id= 7
/dev/sda3 : start= 37495710, size=118800675, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 37495836, size= 15582987, Id=83
/dev/sda6 : start= 53078823, size=102414312, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     8192, size= 16007168, Id= 7
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

---

### Post by caljohnsmith on 2009-02-18
> **shtephutz said:**
> ```
root@MSI:/home/shtephutz# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3640363f

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS
/dev/sda2          411648    37495709    18542031    7  HPFS/NTFS
/dev/sda3        37495710   156296384    59400337+   f  W95 Ext'd (LBA)
/dev/sda5        37495836    [COLOR="Red"]53078822[/COLOR]     7791493+  83  Linux
/dev/sda6        [COLOR="Red"]53078823[/COLOR]   155493134    51207156    7  HPFS/NTFS
```

It looks like your sda6 partition starts at the sector immediately following the sda5 partition, and normally that won't work for logical partitions since they generally need to have an EBR (Extended Boot Record) that comes before the partition (although there are special circumstances where this is not true). Therefore I suspect the start/stop values for your sda6 NTFS partition may be incorrect, and that is what might be causing you the problems. In order to find out, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. Lastly, please post the output of:
```
sudo fdisk -l
```
And we can work from there.

---

### Post by shtephutz on 2009-02-18
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3640363f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        2334    18542031    7  HPFS/NTFS
/dev/sda3            2335        9729    59400337+   f  W95 Ext'd (LBA)
/dev/sda5            2335        3305     7791493+  83  Linux
/dev/sda6            3305        9679    51207156    7  HPFS/NTFS

Disk /dev/sdb: 8199 MB, 8199864320 bytes
233 heads, 4 sectors/track, 17183 cylinders
Units = cylinders of 932 * 512 = 477184 bytes
Disk identifier: 0x22452244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               9       17184     8003584    7  HPFS/NTFS

---

### Post by shtephutz on 2009-02-18
> **shtephutz said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3640363f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        2334    18542031    7  HPFS/NTFS
/dev/sda3            2335        9729    59400337+   f  W95 Ext'd (LBA)
/dev/sda5            2335        3305     7791493+  83  Linux
/dev/sda6            3305        9679    51207156    7  HPFS/NTFS

Disk /dev/sdb: 8199 MB, 8199864320 bytes
233 heads, 4 sectors/track, 17183 cylinders
Units = cylinders of 932 * 512 = 477184 bytes
Disk identifier: 0x22452244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               9       17184     8003584    7  HPFS/NTFS
HMMMMM.....I think I messed something up....
I used once the testdisk utility and tried to fix something by my own..
Now I can see the partition I'm trying to recover data from
but can't mount it because I'm suposed to boot into win_7 OS twice and it's aparently impossible through Grub...my opinion is that i broke that one now...:(....
Anyway now i'll post now the output to teep disc scan:
D HPFS - NTFS              0   1  1   803 254 63   12916197
D HPFS - NTFS              0  32 33    25 159  6     409600
D HPFS - NTFS             25 158 46    51  30 19     409600
D HPFS - NTFS             25 159  6    51  30 42     409600
D HPFS - NTFS             25 159  7  2333 240 19   37083136 [WIN_7]
D HPFS - NTFS             25 159  7  2333 254 63   37084062 [WIN_7]
D HPFS - NTFS            804   0  1  2461 254 63   26635770
D Linux                 2334   2  1  3303 254 59   15582920
* Linux Swap            3304   1  1  3353 254 44     803168
P HPFS - NTFS           3354   1  1  9728 254 63  102414312 [50_GB]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 6613 MB / 6306 MiB
All I want is first to recover my 50_GB partition data and/or start the Win_7 OS 
Thank you for helping and understanding my lack of time to respond...

---

### Post by caljohnsmith on 2009-02-18
> **shtephutz said:**
> 
```

[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1  1   803 254 63   12916197
[COLOR="Red"]P[/COLOR] HPFS - NTFS              0  32 33    25 159  6     409600
[COLOR="Red"]D[/COLOR] HPFS - NTFS             25 158 46    51  30 19     409600
[COLOR="Red"]D[/COLOR] HPFS - NTFS             25 159  6    51  30 42     409600
[COLOR="Red"]D[/COLOR] HPFS - NTFS             25 159  7  2333 240 19   37083136 [WIN_7]
[COLOR="Red"]*[/COLOR] HPFS - NTFS             25 159  7  2333 254 63   37084062 [WIN_7]
[COLOR="Red"]D[/COLOR] HPFS - NTFS            804   0  1  2461 254 63   26635770
[COLOR="Red"]L[/COLOR] Linux                 2334   2  1  3303 254 59   15582920
[COLOR="Red"]L[/COLOR] Linux Swap            3304   1  1  3353 254 44     803168
[COLOR="Red"]L[/COLOR] HPFS - NTFS           3354   1  1  9728 254 63  102414312 [50_GB]
```

OK, using your up/down arrow keys to select each partition shown above, use your right/left arrow keys to mark each partition as shown highlighted in red. If testdisk won't let you mark the last NTFS partition as "L", instead mark it with "P". Once you are sure all the partitions are marked exactly as shown above (or having the last partition marked as "P" if necessary), press enter to get to the next screen, and then choose "Write". Then post the new output of:
```
sudo fdisk -lu
```
After that, how about booting your Windows 7 Install CD, go to the command line, and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find the drive letter for your 50 GB data partition, and then do:
```
chkdsk /r X:
```
Replace "X" with the 50 GB partition drive letter, and run that command as many times as it takes until it reports no errors. Then reboot into Windows/Ubuntu and see if you can access that partition. Let me know how that goes.

---

### Post by shtephutz on 2009-02-18
> **caljohnsmith said:**
> OK, using your up/down arrow keys to select each partition shown above, use your right/left arrow keys to mark each partition as shown highlighted in red. If testdisk won't let you mark the last NTFS partition as "L", instead mark it with "P". Once you are sure all the partitions are marked exactly as shown above (or having the last partition marked as "P" if necessary), press enter to get to the next screen, and then choose "Write". Then post the new output of:
```
sudo fdisk -lu
```
After that, how about booting your Windows 7 Install CD, go to the command line, and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find the drive letter for your 50 GB data partition, and then do:
```
chkdsk /r X:
```
Replace "X" with the 50 GB partition drive letter, and run that command as many times as it takes until it reports no errors. Then reboot into Windows/Ubuntu and see if you can access that partition. Let me know how that goes.

after that last post, I cannot boot into neither one of them. I can try to use live WIN or Live Ubuntu ...grub err 22...
What do you suggest?
I tried by the way to reinstall grub but /boot/grub/stage1 not found...
I should say that the main prob is solved partialy, Wich I have to thank you for..and I am ; I can see my 50_GB in windows and I could backup my files now using my usual live utilities.

---

### Post by caljohnsmith on 2009-02-18
So did you boot your Windows CD and run chkdsk on the 50 GB partition? If so, go ahead and boot your Live CD, and please post the output of the fdisk command from my previous post.

---

### Post by shtephutz on 2009-02-18
> **caljohnsmith said:**
> So did you boot your Windows CD and run chkdsk on the 50 GB partition? If so, go ahead and boot your Live CD, and please post the output of the fdisk command from my previous post.

OK...in a minute..

---

### Post by shtephutz on 2009-02-18
> **shtephutz said:**
> OK...in a minute..

I give up...i'll backup my data and write zeros on my drive and start allover...
it's frustrating...
I can see my 50_gb and the data on it thanks to you.
I think it's better to do it clean and from the start , not to repair the partition table...i'm not so familiar with that...
I thank you for your help and time.
I'm gonna try to solve this tomorrow at work if i'll have the time.
Thank you again and good luck!

---

