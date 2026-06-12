---
title: "is there a way to install ubuntu 7.10 without reformatting my harddrive?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by bigb0i on 2007-10-24
is there a way i can ubuntu without reformatting my whole harddrive so i can keep my windows boot?thanks

---

### Post by subvertigo on 2007-10-24
It is sufficient to have at least 6-7 gigabytes free from partitions...

You can also mantain Windows boot loader, by installing Grub in the Linux partition, instead of in the MBR (default for Ubuntu). The procedure is a bit complicated and it is necessary to use the Alternate CD setup. If you want i can explain how.

---

### Post by kebes on 2007-10-24
> **bigb0i said:**
> is there a way i can ubuntu without reformatting my whole harddrive so i can keep my windows boot?thanks

Yes. You have a couple of options:


1. If you just want to play with Ubuntu a bit, you can boot into the install CD and use it as a "LiveCD". This will let you try Ubuntu without it actually changing your hard drive. However, running off of the CD is slower than a "real" installation, so this is really just to get a "taste" of what it is like.


2. There is a program called "Wubi" that will "install" Ubuntu into a file on your Windows disk, without changing anything else. This will let you run Ubuntu without changing anything. But, again, it's more for testing and is somewhat limited compared to a "real" installation. For more information, check out:
[http://wubi-installer.org/](http://wubi-installer.org/)
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)


3. If you want to fully install Ubuntu, you can still keep your Windows partition, and set up a "dual boot" system. (When you turn on the computer, it asks you which partition you want to boot into: either Ubuntu or Windows.)

During the installation, there will be an option to resize your Windows partition, effectively shrinking it to make room for Ubuntu. That way you can have both Windows and Ubuntu on your hard drive without deleting anything from Windows. (Of course, you must have enough free space on your hard disk for this to work!)

Although the resizing operation should work without losing any data, it's always a good idea to back up your important files before doing something like this!


I hope that helps!

---

### Post by bigb0i on 2007-10-24
Ah thanks a lot guys but can  you guys show me step by step to how install it without reformatting?Thanks

---

### Post by bigb0i on 2007-10-24
Yeah i would like to have a full install of Ubuntu step by step guide please thanks

---

### Post by bigb0i on 2007-10-24
so you're saying when i install ubuntu it will ask me if i want to partition my windows?this is on my laptop btw~thanks

---

### Post by kebes on 2007-10-24
> **bigb0i said:**
> Ah thanks a lot guys but can  you guys show me step by step to how install it without reformatting?Thanks

This is a good step-by-step guide with screenshots:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Don't format your system. Just boot the Ubuntu CD and start the installation process. To get a dual-boot system, when you get to the partitioning step, you pick the option "Guided - Resize partition and use freed space." This will shrink Windows and put Ubuntu into the newly created free space.


That guide is quite explicit, but if you have any questions, feel free to ask.

---

### Post by maharbA on 2007-10-24
It's really very easy. (I was surprised the first time I did it)

Check out this screencast:
[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

(screencasts.ubuntu.com has a bunch of usefull guides)

**It's also a good idea to defragment your Windows hard drive before you resize the partition.**

---

### Post by subvertigo on 2007-10-24
Nevertheless BACKUP YOUR DATA, at least important data.
An error while playing with partition is always possible (and not so unusual).

---

### Post by bigb0i on 2007-10-24
ah thanks guys imma give it a try right now :D

---

