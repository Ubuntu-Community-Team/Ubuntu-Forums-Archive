---
title: "WIreless keyboard stops working when I plug in USB jump drive"
date: 2011-10-07
forum: Hardware
---

### Post by dweebis on 2011-10-07
I was trying to install a firewire card in my system (see below).  Although it was recognized, drives would not mount through it.  I changed the /etc/modprobe.d/firewire-blacklist.conf, and then ran:

sudo update-initramfs -k all -u

When I rebooted, everything was working great.  So I unmounted the firewire, then tried to remount it.  When I did, my wireless keyboard and mouse (Microsoft 6000 with 2.4GHz usb dongle) became very balky.  I decided it wasn't worth it, took out the firewire card, reset the firewire-blacklist.conf file, re-updated my initramfs, and rebooted.  

Everything worked fine, until I plugged in a USB memory stick.  First, the memory stick mounted as two separate drives that I could only unmount in the Diskutility.  Second, my wireless keyboard and mouse once again became almost unusable.  I plugged in a wired keyboard and mouse, and things seem to work fine, but this is clearly sub-optimal.

My question is, how do I get my system back to simply mounting a usb drive and my wireless keyboard and mouse working again (I can live without the firewire).

Thanks

System:
Ubuntu 10.04, kernel 2.6.38-11-generic
Dual Xeon X5660, 2.8GHz
96 Gb Ram
EVGA Classified SR-2 motherboard
256Gb Crucial RealSSD C30
Rocketraid 2720, 5x2TB disks in raid 50
EVGA GeForce GTX 560 Ti video card

---

