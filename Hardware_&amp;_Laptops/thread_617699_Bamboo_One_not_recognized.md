---
title: "Bamboo One not recognized"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by Melodic_BM on 2007-11-19
Hello,
I've got the problem that my Bamboo One isn't recognized as a tablet in my Ubuntu 7.10 Gutsy Gibbon (which provieds out-of-the-box the wacom-7.7.7-drivers). I've installed the newest development files and the stable 07.8.3 files, but the tablet will not be indentified.

The tablet works properly, the light on an it's in the lsusb:
> jonas@jonas-laptop:~$ lsusb | grep Wa
Bus 002 Device 002: ID 056a:0069 Wacom Co., Ltd

In /dev/input/ or /dev/ theres no wacom:
> jonas@jonas-laptop:~$ ls /dev | grep wa && ls /dev/input | grep wa
ptywa
ttywa

In /var/log/messages it's displayed as the following
> usbcore: registered new interface driver wacom
/home/jonas/Desktop/linuxwacom-0.7.8-3/src/2.6.19/wacom_sys.c: v1.46-pc0.1:USB Wacom Graphire and Wacom Intuos tablet driver

The folder linuxwacom-0.7.3-2 doesn't exist anymore on my Desktop so I dont know why the kernel still links on it.

I followed all the tips, including the english and german community forums and the sourceforge-mailing-list archive but I didn't find a solution for my problem.

So may you please help me with my problem.
Thanks,
dusky regards from the cold Germany,
Dauerbaustelle

[--> Same Problem]("http://sourceforge.net/mailarchive/message.php?msg_name=acc1ad140711130615g1f7385fal4e7c89b7abe15858%40mail.gmail.com")

---

### Post by SnakeArtworX on 2008-04-19
I have the same problem. Everything is just as in your case. At #ubuntu channel nobody was able to help me. There's one more thing: after upgrading the kernel to version 2.6.22-14.52 I'm even unable to build wacom sources in version 7.7.7 . I've heard that in Hardy will be a full support for Bamboo, but I'm not sure if Bamboo One has the same construction and uses the same protocol as other types of this tablet.

---

