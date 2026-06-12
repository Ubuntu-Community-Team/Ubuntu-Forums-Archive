---
title: "Hardy Heron Hard Drive Problem (Maxtor IDE)"
date: 2008-05-07
forum: Hardware
---

### Post by Invader Amoto on 2008-05-07
Hello,
My problem is with an IDE Maxtor drive.
Here's my setup:
200GB WDC SATA drive
200GB Maxtor IDE drive (set to primary slave)
LiteOn CD drive (set to primary master(because of physical position of drives in case))

I have my SATA drive partitioned with a swap, my / filesystem, and an NTFS partition(empty). My IDE drive has one ext3 partition which I added to /etc/fstab with this line:
"
UUID=77304871-78c0-4c2b-a061-6cfa6629e16a	/home/john/Storage	ext3	user,exec,auto,rw	0	2
"
It works perfectly, and I can read and write files, but sometimes it randomly just stops working and doesn't come back until I reboot. It says its mounted in nautilus and i can browse (some of) the files. Any application i use to open any of the files just freezes until i force quit it. Trying to unmount it from nautilus freezes nautilus and the only fix is restarting the computer. If i try to umount it from terminal, i get:
"umount: /home/john/Storage: device is busy
umount: /home/john/Storage: device is busy" (ya, twice, is it supposed to do that?)
I attached a segment of my system log messages starting right when the problem started.

Forgot to mention: it keeps repeating the stuff in system log over and over again. Also I've had this problem for a while, since hardy heron came out. All this hardware worked perfectly with gutsy.

---

### Post by Invader Amoto on 2008-05-08
Bumpity Bump...

---

### Post by Invader Amoto on 2008-05-09
Bump...again.

---

### Post by prshah on 2008-05-09
> **Invader Amoto said:**
> randomly just stops working and doesn't come back until I reboot. 

See [http://ubuntuforums.org/showthread.php?t=625076](http://ubuntuforums.org/showthread.php?t=625076) (Unsolved) for tips...

---

### Post by Invader Amoto on 2008-05-10
Well, I've solved my problem. All I did was switch the CD drive to slave and the Hard Drive to master (took a little ide cable twisting) and now everything works fine. I've had the old setup working with Gutsy for a while now. I guess Hardy doesn't like that setup.

-Invader Amoto

---

