---
title: "General Partitioning Questions"
date: 2008-06-18
forum: Hardware
---

### Post by AcerAspirant on 2008-06-18
I've just installed Ubuntu onto an ext3 partition on my Acer Aspire 5600, my main partition is XP on NTFS, and I followed [these tips](http://www.psychocats.net/ubuntu/partitioning) and so also set up a swap area and a /home partition.  However, I have some left over space (25 gigs) that I want to use as shared space, but I can't seem to format it as FAT32.  Did I run out of partitions?  Also, how do I access the different partitions from each other?  Finally, what are the best free/open-source partition software in Ubuntu and Linux?

---

### Post by sksurhio on 2008-06-18
Are you using duel boot?
If yes, you don't need any software becouse WinXP(i say Win bacause i think you are much known about as begginers).
Just go to this directory "..Windows/system32", there you'll see diskmgmt.exe, run it and you'll see unused partiotion there. Right-click on that and select create partition and use proper options.
In UBUNTU, m also beginner so SORRY from me.
If any person know how to do so in UBUNTU please let us know.

---

### Post by Odrodzona-Sarmacja on 2008-06-18
> **AcerAspirant said:**
> Finally, what are the best free/open-source partition software in Ubuntu and Linux?

Gparted. It is as good as Partition Magic on windows.
If you can't use it from inside of Ubuntu to format that free space, then use Gparted livecd.

---

### Post by AcerAspirant on 2008-06-21
Is there a limit to how many primary partitions I can have?

Also, how do I actually access/use the share partition?

---

### Post by uidb4056 on 2008-06-21
Yes you can have only 4 primary partition on one disk, you can use the free space to grow one of your partitions or delete one primary and create an extended partition instead of primary.

---

### Post by chungy on 2008-06-21
There's no reason for a FAT32 share partition.  Ubuntu can read/write NTFS out of the box, and you can read/write ext2/3 from Windows by downloading a driver from here: [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by louieb on 2008-06-21
> **uidb4056 said:**
> Yes you can have only 4 primary partition on one disk...create an extended partition
Some partition basics. max of of 4 primary or 3 primary + 1 extended partitions. The extended partition partition was invented to get around the 4 partition limit. Inside the extended you create logical partitions. (up to 15 on a sata drive - more that that on an ide drive).

To help see how your setup -  please post your partition table - open Applications>Accessories>terminal. and post the output of 
```
sudo fdisk -l
``` (lower case L at the end). 

Can't say how to access it until you know what file system you put on it. Use windows more? NTFS or Linux more? - ext3. 
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

Having a separate data partition is the  smart way to go. Makes it easy to backup your data. And it keeps it out of the way if you have reinstall one of your OS.

---

### Post by AcerAspirant on 2008-06-23
Here you go:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe121737f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2           12572       14593    16241715   83  Linux
/dev/sda3           12511       12571      489982+  82  Linux swap / Solaris
/dev/sda4            8925        9592     5365710   83  Linux

Partition table entries are not in disk order

---

### Post by AcerAspirant on 2008-07-02
Er... any suggestions?

---

### Post by AcerAspirant on 2008-08-07
please help

---

### Post by mc4man on 2008-08-07
It's easier to see from afar if you run fdisk like this
```
sudo fdisk -lu
```

---

### Post by AcerAspirant on 2008-08-16
Thanks, well here it is:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe121737f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143364059    71681998+   7  HPFS/NTFS
/dev/sda2       201953115   234436544    16241715   83  Linux
/dev/sda3       200973150   201953114      489982+  82  Linux swap / Solaris
/dev/sda4       143364060   154095479     5365710   83  Linux

Partition table entries are not in disk order

Disk /dev/mmcblk0: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             255     3932159     1965952+   6  FAT16

So, which partition can I use as a place for shared data between Ubuntu and XP, and how do I access that partition when I'm in either OS?

---

### Post by AcerAspirant on 2008-08-29
Alright, alright, fine I'll just delete Ubuntu and stick with XP then, thanks guys.

---

### Post by AcerAspirant on 2008-09-22
At least with Windows when you pay money you'll get actual results and answers.

---

### Post by AcerAspirant on 2008-09-26
Dicks

---

### Post by AcerAspirant on 2008-11-11
Butts

---

### Post by Jeo_fin on 2008-11-11
In ubuntu you can mount this partition. Just make folder like /share (root folder)
Command (X is partition number that you want to mount)
```

(sudo) mount /dev/sdaX /share

```
other usefull command is
```
gparted
```
which shows graphical version of partitions.
And if everything was all right shared drive should be in /share.
You can make this a script to the desktop so just double-clicking is enough. Or you can place it in autostart.
[This might be usefull.]("https://help.ubuntu.com/community/Mount")
About windows's I dont know but I think that it MEABY founds this partition automaticly (download that file)..

I have ubuntu/ZenWalk dualboot with shared /home & swap partitions and no (real) problems.
Feel free to contact me thru MSN (lammas85 MIUMAU hotmail dot com) or with email (same but _gmail dot com_)

---

