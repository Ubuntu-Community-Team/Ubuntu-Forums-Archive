---
title: "MA521 on Ubuntu with Driverloader issues!"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by Enzo386 on 2004-12-26
Hello, i'm trying to get my MA521 Netgear Wireless card to work on Ubuntu. I found out i need driverloader to get it to work, but when i try to install driverloader it says i need the kernel source. I have no internet except my wireless so i can't download the kernel source! Does NDIS Wrapper need kernel source also? If not can anybody give me a quick tutorial on how to do it? I'm deseperate, i hate windows and i want to use linux on my laptop but if my wireless doesn't get working i'll have to go back to windows :(

---

### Post by Enzo386 on 2004-12-27
Does anybody have any ideas? i need help please  :sad:

---

### Post by Soulman on 2004-12-29
Have a nice look at ndiswrapper.  Looking at their supported hardware I found this:

Card: Netgear MA521
Chipset: RTL8180 FCC_ID: PY3MA521
Driver: ftp://210.51.181.211/cn/wlan/rtl8180l/ndis5x-8180(170).zip (NOT NETGEAR DRIVER! NETGEAR DRIVER UNSTABLE!!)
Other: Works well even with DHCP on SUSE 9.0 Pro. 128 bit wep, managed mode. Will be trying WPA/PEAP/MSCHAP v 2 sometime later on. Check [http://hastingswireless.homeip.net/index.php?page=articles&number=2004.11.22](http://hastingswireless.homeip.net/index.php?page=articles&number=2004.11.22) for information.

So looks like there is hope after all and also take a good look at their install wiki.  Good luck!

ndiswrapper.sourceforge.net

---

