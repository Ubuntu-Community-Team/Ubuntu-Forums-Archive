---
title: "Help needed, want to install windows xp"
date: 2008-09-13
forum: General Help
---

### Post by sameer.tahseen on 2008-09-13
Dear Friends

I have a ubuntu 7.10 installed on my machine,and now i want to install a copy of win xp on a different partition,
But every time i want to install, after getting to the part of disks and partitions window, it gives the message,
Unknown Disk
There is no disk in this drive.

Although i know that the drive exists and it is formatted with gparted to ntfs.

Guys it's urgent plz help me, am waiting!!!!!!!!!!!

Actually i have a hd of 120 GBs, one partition that have linux is holding 78 GBs and the other one (for windows) is holding 40 GBs.

---

### Post by ronnielsen1 on 2008-09-13
Personally, when I tried this Windows didn't recognize the ntfs partition that linux created.
It would probably be better to let windows do it's own formatting but I think windows needs to be on the 1st partition

---

### Post by caljohnsmith on 2008-09-13
From Ubuntu, how about posting the output of:
```
sudo fdisk -lu
```
That will tell us how you have your partitions set up right now.

---

### Post by nacho32 on 2008-09-13
I found it works better to install xp first less of a hassle.
I did  Xp vista then ubuntu.

---

### Post by sameer.tahseen on 2008-09-13
Dear CaljohnSmith
this is the outcome of the command you said, really plz reply back, i am hoping that finally i will get an answer....
Thnx

outcom of fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e51cda9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *    78124095   228428234    75152070   83  Linux
/dev/sda3       228428235   234436544     3004155    5  Extended
/dev/sda5       228428298   234436544     3004123+  82  Linux swap / Solaris

Actually i have a hd of 120 GBs, one partition that have linux is holding 78 GBs and the other one (for windows) is holding 40 GBs.

---

### Post by fourthofjuly on 2008-09-13
> **sameer.tahseen said:**
> Dear CaljohnSmith
this is the outcome of the command you said, really plz reply back, i am hoping that finally i will get an answer....
Thnx

outcom of fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e51cda9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *    78124095   228428234    75152070   83  Linux
/dev/sda3       228428235   234436544     3004155    5  Extended
/dev/sda5       228428298   234436544     3004123+  82  Linux swap / Solaris

Actually i have a hd of 120 GBs, one partition that have linux is holding 78 GBs and the other one (for windows) is holding 40 GBs.
you don't seem to have any ntfs partitions...?

pl resize the ubuntu partition to make space and create a new ntfs partition for XP...

more importantly, if you want a dual boot system, XP if installed AFTER Ubuntu will take over and not allow you to boot Ubuntu...!

---

### Post by kokkus on 2008-09-13
Download and install vista insted. As I can remember when a friend of me installed vista on a ubuntu pc, vista will do this automaticly.
So if u want xp on your PC insted, download and install vista and overwrite it with xp. I guess this is the safiest way if you don't wanna lose data (just in case).

---

### Post by caljohnsmith on 2008-09-13
Like fourthofjuly said, you don't have an NTFS partition on your HDD at this point. You'll need to resize sda2 so that you can create another partition. Make sure you create a primary partition, and not a logical one, as Windows should be installed to a primary partition if you want to minimize your troubles. And as fourthofjuly alluded to, once you install Windows, it will install its own master boot record and prevent you from using Grub and Ubuntu. Once you have Windows successfully installed, you can reinstall Grub to the master boot record by booting up a Live CD and doing:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let us know how it goes.

---

### Post by lukjad on 2008-09-13
Try this link:
[http://thevistaforums.com/index.php?showtopic=19902](http://thevistaforums.com/index.php?showtopic=19902)

---

### Post by bhogal on 2008-09-13
Hello,

I also had the same problem before. What i did was that i formated my drive and first install Windows XP and then Install Ubuntu. When you Install Windows XP, Let Windows doing the formating into NTFS. After install Ubuntu and you can resize the Windows Partition, when you are installing Ubuntu. 

I did Partition my drive as follows

c: windows NTFS
   SWAP
   Ubuntu ext3

Try this, it might help, it works fine for me. Saved me alot of hassle. Well even if zou are able to install windows XP after you have install Ubuntu. Windows will rewrite your boot loader. So it is always better to install windows first.

Hope it works for you

---

