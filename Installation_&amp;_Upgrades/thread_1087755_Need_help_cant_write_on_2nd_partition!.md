---
title: "Need help cant write on 2nd partition!"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by klnyc on 2009-03-05
Hi gurus,


    I have a Ubuntu installed on Asus Eee PC with a 40gig SSD drive.
My problem is I can not write on my 2 partition that I created. The drive is mounted and I can open up, I see  a Lost n Find folder, but I can drag or save anything in there.

sudo fdisk -  l : I get this
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c5a08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

Disk /dev/sdc: 8067 MB, 8067743744 bytes
217 heads, 4 sectors/track, 18153 cylinders
Units = cylinders of 868 * 512 = 444416 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              10       18154     7874560    b  W95 FAT32


anyhelp appreciated.
ken

---

### Post by logos34 on 2009-03-05
I think all you need to do is chown it:

sudo chown -R username:username /mount/point

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(--> bottom)

---

### Post by klnyc on 2009-03-05
> **logos34 said:**
> I think all you need to do is chown it:

sudo chown -R username:username /mount/point

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(--> bottom)

i got this:
tim@GHOST-MBL:~$ sudo chown -R tim /mount/dev/sdb1
chown: cannot access `/mount/dev/sdb1': No such file or directory
tim@GHOST-MBL:~$ cd /dev/sdb1

---

### Post by klnyc on 2009-03-05
lol, i got mounted now.
another question...I used to see 32gig hard dive on my desktop top. now is gone.  How do i get it back.. Sorry, this such a noobie q.

---

