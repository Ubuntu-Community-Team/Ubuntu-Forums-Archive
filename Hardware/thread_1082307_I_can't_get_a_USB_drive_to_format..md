---
title: "I can't get a USB drive to format."
date: 2009-02-27
forum: Hardware
---

### Post by grs on 2009-02-27
I'm trying to setup a 500GB usb drive on my linux pc. It had been on a windows PC before. I need it to rescue some data from another drive with testdisk.

When I go through the fdisk process it goes till I try to write the changes.
An error message comes up saying something about logfile indicates unclean shutdown and that I need a windos pc to correct the problem.

How can I get passed this without a windows pc? I would have thought as its been reformatted all that sort of detail would not matter.

---

### Post by TenPlus1 on 2009-02-27
Maybe this will help: [http://ubuntuforums.org/showthread.php?t=687376](http://ubuntuforums.org/showthread.php?t=687376)

---

### Post by caljohnsmith on 2009-02-27
"fdisk" will just let you set up partitions, it won't actually format the partitions. Have you tried using gparted to format the drive? You can install it with:
```
sudo apt-get install gparted
```
And it will show up under System > Admin > Partition Editor. It comes with the Live CD if you want to use from there. Good luck and let us know how it goes.

---

### Post by grs on 2009-02-28
> **caljohnsmith said:**
> "fdisk" will just let you set up partitions, it won't actually format the partitions. Have you tried using gparted to format the drive? You can install it with:
```
sudo apt-get install gparted
```
And it will show up under System > Admin > Partition Editor. It comes with the Live CD if you want to use from there. Good luck and let us know how it goes.

I got it mounted and running fine. Thanks. If any of you know about testdisk and data slavage I have another thread at [http://ubuntuforums.org/showthread.php?t=1076505]("http://ubuntuforums.org/showthread.php?t=1076505") any help would be great.

---

