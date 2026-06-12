---
title: "which hard disk should i use?"
date: 2008-08-01
forum: General Help
---

### Post by Ginoxy on 2008-08-01
hello 
i have the following hard disks which one should i use? 

---
Disk /dev/sda: 40.9 GB, 40971571200 bytes
255 heads, 63 sectors/track, 4981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1aeb1ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sda2            3825        4980     9285570    f  W95 Ext'd (LBA)
/dev/sda5            3825        4980     9285538+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa56c6ed7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2727    21904596    7  HPFS/NTFS
/dev/sdb2            2728        4910    17534947+   7  HPFS/NTFS
/dev/sdb3            4911        7842    23551290    7  HPFS/NTFS
---

---

### Post by Elfy on 2008-08-01
No idea - what do you want to use it for exactly ;)

---

### Post by phidia on 2008-08-01
What do you want to get rid of? It looks like those drives have partitions with windows filesystems. Just use what works best for you and be sure to back up anything you don't want to lose-just a precaution.

---

### Post by Ginoxy on 2008-08-01
i have windows XP and i have Wubi installed \
but i want ubuntu to be completely installed in another space

---

### Post by Elfy on 2008-08-01
You can migrate the wubi installation if you wish

[https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

This is the wubi guide

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

As it stands it would seem that windows is on sda - you have I assume data or other things on the other drive sdb

---

### Post by Ginoxy on 2008-08-01
yeah but i want windows XP not to remove it ! 
well the data which is there on the other drive are some musics and movies and some word files.

---

### Post by Paqman on 2008-08-01
> **Ginoxy said:**
> i have windows XP and i have Wubi installed \
but i want ubuntu to be completely installed in another space

All you need to do is make enough room for LVPM to transfer the Wubi installation into. You'll need a main partition of 10-20GB, plus a small swap partition equal to the size of your RAM. It doesn't really matter where you put them. The LVPM site has guides on how to achieve this.

---

### Post by kansasnoob on 2008-08-01
There's no way to tell from that!

But personally I prefer having both (or more) operating systems on the same drive while assigning all other drives as storage.

But, with four hard drives you should google LVM.

Basically it's like folks coming to me asking what it will cost to fix their motor home. Yeah I used to do that! My answer to them, "If you need to ask you can't afford it"!

My answer to you is, "If you need to ask, don't try it"!

---

### Post by phidia on 2008-08-01
The reason any of us ask questions is so we can learn.

There is no problem here with asking questions and asking does not mean you can't try to do what you're asking about.

---

### Post by kansasnoob on 2008-08-01
> **kansasnoob said:**
> There's no way to tell from that!

But personally I prefer having both (or more) operating systems on the same drive while assigning all other drives as storage.

But, with four hard drives you should google LVM.

Basically it's like folks coming to me asking what it will cost to fix their motor home. Yeah I used to do that! My answer to them, "If you need to ask you can't afford it"!

My answer to you is, "If you need to ask, don't try it"!

I guess my response was perhaps course and abrupt!

My concern is that you have four hard drives! Lots of data! I want to be absolutely sure that you DON'T go at this in a "willy-nilly" manner!

We far to often hear from folks that lost things they didn't want to lose or end up with a system or OS that won't boot.

I was very serious about the LVM thing! It gets tricky! You can end up in a situation where you need to install GRUB to each drive just to be able to boot each drive!

I only meant to warn you that what you're looking at is NOT simple! Well, with both operating systems on the same drive it shouldn't be too bad.

Sorry if I seemed rough!

---

### Post by phidia on 2008-08-01
Hey kanasnoob, I'm not trying to be the PC police even though I'm doing a bad job of that (insert werid laughter here) Just want everyone including me to feel free to ask questions.

And please take a look at the ouput of the 1st post here. I believe, if you look carefully, that there are only two drives listed. That is each drive is called out and under that the partitions each drive contains.

---

### Post by Ginoxy on 2008-08-02
Hi again well i just used LVM and i just resize and increase the space but i go this 

[ATTACH]79840[/ATTACH]

now i should rename it to root.disk 

but since i already have one so how can i add the 5GB to the rest of the space?

[ATTACH]79841[/ATTACH]

---

