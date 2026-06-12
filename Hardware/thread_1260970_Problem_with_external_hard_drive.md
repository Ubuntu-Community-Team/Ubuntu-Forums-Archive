---
title: "Problem with external hard drive"
date: 2009-09-08
forum: Hardware
---

### Post by johnstinkpants on 2009-09-08
Hi all

I'm not that great with computers and was hoping to use ubuntu to recover files from my dead laptop. I'm running ubuntu from a cd and can see all my files. I was hoping to use my external HDD to get all my files off the laptop, but when I plug it in to the usb port nothing happens and ubuntu doesn't seem to recognise it. I've read a few threads about needing to mount it but I don't really understand it to be frank.

I'd be very grateful if anyone could post a noob guide on how to do this (if this is indeed what needs to be done). I have no experience with ubuntu whatsoever.

---

### Post by Jose Catre-Vandis on 2009-09-08
First, open a terminal
next run the following command:
```
fdisk -l
```
This will output the file systems and disks you have. Identify the External HDD (probably something like /dev/sdb or /dev/sdb1

Next create a mount point
```
mkdir /media/ExHDD
```
and finally mount
```
mount /dev/sdb1 /media/ExHDD
```

Head back to Nautilus/Thunar/whatever and you should find you are all mounted up and ready to transfer files.

Of course, if your External HDD does not show up in fdisk, you have a different problem!

---

### Post by johnstinkpants on 2009-09-08
Thanks for the quick reply -just one more noob question -how do I open a terminal?

---

### Post by Whiffle on 2009-09-08
Applications > Accessories > Terminal

---

