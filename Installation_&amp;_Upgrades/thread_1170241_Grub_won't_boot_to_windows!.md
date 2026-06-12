---
title: "Grub won't boot to windows!"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Lepy on 2009-05-26
So, I got a new 500 gig WD Caviar Black that is quite speedy and wanted to use it as my OS drive.

I installed  WinXp and then Win7RC (recognized as sdc5 and sdc6 respectively in gparted) and used gparted's copy function to transfer my Ubunty 32 and 64 bit installs as well as my home folder to ext3 partitions I created on the Caviar (recognized as sdc9, sdc10, and sdc8 respectively). I used the remaining space as an ntfs partition for storage/program installs until I can get my 1TB Raid 1 setup.

After all of this, I used to the gparted CD to mount my 32bit install (sdc9), found the grub menu, and installed it on the mbr of the 500gig. 

Now, both the 32 and 64 bit ubuntu installs are recognized, boot up, and share the home folder flawlessly, but I can't get the right menu.lst setting to let the windows installs boot. Instead I get an "Error 12: Invalid device requested" message no matter the combination I try.

sudo fdisk -l gives me this for the WD Caviar:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       12058    96847852+   f  W95 Ext'd (LBA)
/dev/sdc2   *       12059       60801   391528147+   7  HPFS/NTFS
/dev/sdc5               2        1403    11261533+   7  HPFS/NTFS
/dev/sdc6            1404        5228    30724281    7  HPFS/NTFS
/dev/sdc7            5229        5483     2048256   82  Linux swap / Solaris
/dev/sdc8            5484        8670    25599546   83  Linux
/dev/sdc9            8671       10455    14337981   83  Linux
/dev/sdc10          10456       12058    12876066   83  Linux

```

I hope I have just missed something simple as I do not want to have to transfer or install 4 different operating systems again, having wasted enough time.

---

### Post by logos34 on 2009-05-26
you tried 

root (hd0,1)

?

is the 500 gb set as your boot disk in the bios?

---

### Post by Lepy on 2009-05-26
logos, I can't thank you enough!

Your suggestion was just the trick. Now, selecting the windows grub entry calls up the windows7 boot menu, allowing me to access xp or the release candidate.

The 500 gig was always set as the 1st boot HDD in the bios, and I know I tried (hd0,0), (hd0,4), and (hd0,5), but I guess I had never thought to try the partiton marked boot (/dev/sdc2 = root(hd0,1), well DUH?!?!).

I've been playing with Ubuntu for a few months now, but there is always something new to learn. Thanks again!

---

### Post by logos34 on 2009-05-26
glad to help.  

This confuses a lot of people.  Whenever you install windows on *logical* partitions inside an extended partition (sdc1), what happens is the windows installer looks for an ntfs or fat32 PRIMARY partition to put the boot files on so windows bootloader (on the MBR) can find it (it only searches primary partitions). 

There's no way to prevent windows from doing this, even if you're using grub or another bootloader to chainload windows. (well, there is something called 'hide', but that's for two windows partitionms on primary partitions).  Anyway, that's basically what's happening. 

enjoy

---

