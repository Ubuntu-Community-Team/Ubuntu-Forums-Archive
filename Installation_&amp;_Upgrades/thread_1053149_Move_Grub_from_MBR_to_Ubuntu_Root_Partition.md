---
title: "Move Grub from MBR to Ubuntu Root Partition?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by krt on 2009-01-28
Having screwed up and put grub in the MBR of my hard drive where it dual boots Windows XP and Ubuntu, is there any way to move it to the root partition of Ubuntu 8.04.2 so that I can use an alternative boot loader, or do I have to do a reinstall?

I ask this because I wasted several hours personalizing my installation before I found a thread here that explained how to set up the partitioning so that Grub is indeed installed in the Ubuntu root partition.

Thank you,

krt

---

### Post by Elfy on 2009-01-28
You can reinstall grub to it's partition yes - but I would assume that you'd need to make sure you install whatever bootloader you are going to use first.

Boot with the livecd - then in a terminal

```
sudo grub
grub> find /boot/grub/stage1
```

it will return with something like hd(0,1) - use that in the next commands

```

grub> root (hd0,1) 
grub> setup (hd0,1) 
grub> quit
```

That will install grub to the buntu partition.

---

### Post by krt on 2009-01-28
Thanks.  That worked great.  After installing 3rd party bootloader, I then commented out the lines for Windows, and I was/am in business.

Really appreciate your help; a search before I posted showed all sorts of things about modifying menu.lst to change loading order and time, etc., but not how to move it to the actual Ubuntu root partition.

krt

---

### Post by Daeluin on 2010-01-11
thanks, just what I needed.

---

### Post by weizguy on 2010-01-22
How can I make this work with Ubuntu 9.10 Grub2?

---

### Post by efflandt on 2010-01-23
For grub2 see [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) and scroll down to where it says "Recover grub2 via live CD".  Although, if you can boot your current system, you do not need the live CD and chroot.  Just boot into your system, and for example if you wanted it on sda2, you could do **sudo grub-install /dev/sda2** (ignore the warning that it might not work).  Then you would need to restore your mbr to standard mbr and mark sda2 as the boot partition.

I did that on my desktop because when I first installed Ubuntu it gave no clue that it was going to overwrite your mbr.  I know it works with grub2 installed on a primary partition, but I have not tested it on an extended partition or logical partition (I think lilo used to work on either primary or extended partition).

---

### Post by krt on 2011-03-16
I just tried this on Ubuntu 10.04 and it did not seem to work:

1.  I had to use --force because it told me it was such a bad idea that it would not do it since it required blockfiles unless I used --force.
e.g.: **sudo grub-install --force /dev/sda6**
rebooted and grub2 was still in MBR, so I repeated the above and added then as second command:
**sudo update-grub**
I tried this with working installation because I had already tried the scheme described above from live disk (which worked with old 8.04) and it refused to do anything from sudo running live . . . ?

What am I doing wrong?  

To repeat the question, I want to move GRUB2 from MBR to the Ubuntu root partition on sda6 in Ubuntu 10.04.

Thank you,

krt

---

