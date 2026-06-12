---
title: "XP Dual Boot Set Up (All this helped me)"
date: 2008-07-14
forum: Hardware
---

### Post by ElvetPuff on 2008-07-14
Hi guys,

Today was the day I finally installed Ubuntu. I had a few problems along the way, but I got there eventually. Anyway, all of the following helped me, so I thought I'd share:

MY LAPTOP:

Dell Inspiron 6400

Core Duo @ 1.6 Ghz
512 MiB RAM
60 GB HDD
Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Card
Broadcom 1390 WLAN Card
...

(I'm assuming you have internet access.)

THINGS THAT HELPED ME:

HARDDRIVE

GParted kept telling me my harddrive had bad sectors and that it couldn't read it and running chkdsk from Windows didn't help (nor did ntfsfix). But the following program worked for me:

Paragon Partition Manager (Personal Trial) 
[http://www.partition-manager.com/](http://www.partition-manager.com/)

WLAN CARD

The following guide helped me, with one slight difference. I had to manually download the b43-fwcutter package myself, the terminal command didn't work.

[http://flavor8.com/index.php/2008/06/08/howto-broadcom-1390-wireless-on-ubuntu-hardy/](http://flavor8.com/index.php/2008/06/08/howto-broadcom-1390-wireless-on-ubuntu-hardy/)

GRAPHICS CARD (for Compiz)

Before I followed this guide the 'extra' compiz features didn't really work properly (windows got stuck and other small, annoying bugs). Now everything is fine:

[http://grumpymole.blogspot.com/2008/03/ubuntu-hardy-intel-945-graphics-driver.html](http://grumpymole.blogspot.com/2008/03/ubuntu-hardy-intel-945-graphics-driver.html)

INSTALLING GCC

Just run this:

sudo apt-get install gcc build-essential

I really hope this helps someone - I know if I'd found a post like this before I started my install I would have saved a lot of time!

--ElevetPuff

---

