---
title: "Jaunty: Toshiba Satellite M45 can't change screen brightness"
date: 2009-08-06
forum: Hardware
---

### Post by cupoange on 2009-08-06
running jaunty and i've tried all the usual remedies and done a bunch of searching.  gnome applet does nothing, power management does nothing.  when i unplug ac adapter the icon shows half brightness but there is no change.  

any suggestions?

---

### Post by aharown07 on 2009-08-16
I'm having this problem also... M45 s331 Toshiba.

---

### Post by rygar on 2009-09-26
m45 s355, same problem.  still no ideas?

---

### Post by aharown07 on 2009-10-04
No solutions on my end.
My m45 has alot of miles on it and has acpi problems anyway, so I don't use it for much.

---

### Post by rygar on 2009-10-20
Hey guys,

I managed to solve the problem on my computer.  I'm using Karmic beta right now, but I think it should work with Jaunty.  It involves installing the omnibook module, which previously worked for me under Feisty, but was very convoluted.  Anyway, enough talk, here's how to do it:

Download the latest omnibook SOURCE deb from
[http://packages.kirya.net/debian/pool/main/o/omnibook/](http://packages.kirya.net/debian/pool/main/o/omnibook/)
(currently omnibook-source_2.20070211+svn20090714b-1_all.deb)

Install prerequisites:
sudo apt-get install build-essential linux-headers-`uname -r`

Double click on the .deb, Install

cd /usr/src
sudo tar xjvf omnibook.tar.bz2
cd modules/omnibook
sudo make install
sudo depmod -a
sudo modprobe omnibook

gksudo gedit /etc/modules

Add a new line to the bottom that says "omnibook" (minus the quotes)

Save file, re-start your computer, voila!

Now as long as it's enabled in Power Management, your computer should dim when it's on battery power and brighten when its plugged in.

You can also manually change brightness by:
cd /proc/omnibook
sudo su
echo 0 > lcd

(where 0 is the dimmest and 7 is the brightest)

Note that this does NOT enable your brightness hotkeys.  If anyone can help with that, please do!

Hope this helps someone!!  

Sources: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021)

---

