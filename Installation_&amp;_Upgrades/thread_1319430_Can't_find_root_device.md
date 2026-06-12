---
title: "Can't find root device"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by ronmaroria on 2009-11-08
I upgraded from 9.04 to 9.10 using the upgrade manager. When i try to reboot, i consistently get the message:

"gave up waiting for root device. Common problems:
-boot args (cat /proc/cmdline)
   -check root delay =
   -check root
-missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ef370d05-5064-4306-9539-2f714b7840b does not exist" 

then it drops back to the initramfs prompt.
Note that i have edited my /etc/menu.lst timeout to 120 as suggested else where, also the menu.lst lists the same uuid as the one that does not exist, supposedly. If it helps, i am running a 64-bit system.

---

### Post by AndreLeComte on 2009-11-08
I have the same issue although I can boot using the 2.6.28 kernel. Does that help?

---

### Post by usaar33 on 2009-11-08
> **ronmaroria said:**
> I upgraded from 9.04 to 9.10 using the upgrade manager. When i try to reboot, i consistently get the message:

"gave up waiting for root device. Common problems:
-boot args (cat /proc/cmdline)
   -check root delay =
   -check root
-missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ef370d05-5064-4306-9539-2f714b7840b does not exist" 

then it drops back to the initramfs prompt.
Note that i have edited my /etc/menu.lst timeout to 120 as suggested else where, also the menu.lst lists the same uuid as the one that does not exist, supposedly. If it helps, i am running a 64-bit system.

32-bit here and same issue.
Do you have anything in /dev/disk/by-uuid? (or does that directory even exist?)

---

### Post by ronmaroria on 2009-11-09
The directory " /dev/disk/by-uuid " does not exist in my system.

---

### Post by arekku on 2009-11-09
Hey I might be able to help you.
Or rather [this guy](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html).

My theory is someone botched up and didn't include SATA drivers, and you have a SATA drive.

By using a old initramfs-something image it should detect SATA drives. I can't attach my 32 bit (working) files due to size constraints, but if you need them I can mail them to you.

---

### Post by AndreLeComte on 2009-11-09
arekku basically solved the issue for me, thanks!!:

> **arekku said:**
> [Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

### Post by usaar33 on 2009-11-09
I have the same issue as ronmario where by-uuid doesn't show.  

There is no /boot in the busybox terminal.  

None of my kernels work, so I can't boot up to access such commands (I unfortunately also have a broken cdrom drive, so I can't use a live cd).

---

### Post by ronmaroria on 2009-11-14
tried that and it did not work!

---

### Post by cpttripzz on 2009-12-14
Solved*

I had the same issue. I fixed this issue by chrooting into the old root directory

see this article [http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

and then running sudo apt-get update; sudo apt-get dist-upgrade

Hope this helps everybody else with this problem.

---

