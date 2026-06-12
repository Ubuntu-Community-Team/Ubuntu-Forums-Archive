---
title: "Grub Error 17 plus Cannot Open /dev/sda"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by navjotjsingh on 2009-01-28
I have two problems combined,

I have a 250GB HDD with XP installed on C using some 74GB Parition.

Second Parition of approx the same size was empty and third remaining contains lots of data.

Now I deleted the second empty parition and Separated 49 GB and the rest. Of the rest, I used 30GB for /boot and 2GB for /swap and installed Ubuntu 8.10 on it.

Ok..this went smoothly. I restarted with Grub loading properly and booted into XP.

Now ... I didn't realise this but after booting into XP, I opened diskmgmt.msc and allocated the empty 49GB parition and quick formatted it as NTFS.

ANd now after restarting the PC, grub does not load saying error 17.

I tried booting from Live CD, Went to Terminal and used the following command:

```
fdisk -l
```

And it showed:

```
Cannot Open /dev/sda/
```

I also tried:

```
cat /proc/partitions
```

Which shows the following output:

```
major minor  #blocks  name

   8     0  244198584 sda
   8     1   81923436 sda1
   8     2          1 sda2
   8     5  850995205 sda5
   8     6    1951866 sda6
   8     7    9767488 sda7
   8     8   42957778 sda8
   8     9   78292746 sda9
   7     0     691600 loop0
```

Now pls help me gaining back into my system without any data loss. Any idea?

---

### Post by caljohnsmith on 2009-01-28
If your Ubuntu is a fresh install, can you just reinstall it? That would most likely fix the problem. Or is there some really important data in your Ubuntu partition you want to try and recover? If so, how about posting:
```
sudo fdisk -lu
sudo blkid -c /dev/null
```
And please identify your partitions.

---

### Post by navjotjsingh on 2009-01-28
Yes...It was a fresh install...so at present I have used my XP CD and used fixboot and fixmbr commands to regain access.

Though Strangely...I never saw such errors being reported anywhere on net. fdisk -lu Also returns nothing. Neither there was any grub folder in the existing Installation of Ubuntu. I was able to mount all partitions using Live CD but Partition Editor or sudo commands failed to show any parition.

Well..I hope I never get into this tricky situation again.

---

