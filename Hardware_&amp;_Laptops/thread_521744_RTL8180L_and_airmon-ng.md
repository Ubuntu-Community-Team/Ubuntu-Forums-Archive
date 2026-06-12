---
title: "RTL8180L and airmon-ng"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by turboCRO on 2007-08-09
can't get this to work with my card ...
to enable monitor mode I must install these drivers, but, I run into errors..

ifconfig wlan0 down
rmmod r8180
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
wget [http://patches.aircrack-ng.org/rtl8180-0.21v2.patch](http://patches.aircrack-ng.org/rtl8180-0.21v2.patch)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
patch -Np1 -i ../rtl8180-0.21v2.patch
make && make install
depmod -a
modprobe r8180

second line gave me this error

ERROR: Module r8180 does not exist in /proc/modules



last command error:

FATAL: Error inserting r8180 (/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/r8180.ko): No such device


I see connection between r8180 module and r818x module but don't know how to solve this
also airmon-ng give me this output:


turbo@turbo-desktop:~$ sudo airmon-ng start wlan0 1

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wlan0           Unknown         Unknown (MONITOR MODE NOT SUPPORTED)

can anybody help me ?
Ubuntu 7.04 clean install

thanks

---

