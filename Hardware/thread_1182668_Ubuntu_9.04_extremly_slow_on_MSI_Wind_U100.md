---
title: "Ubuntu 9.04 extremly slow on MSI Wind U100"
date: 2009-06-09
forum: Hardware
---

### Post by Aleks` on 2009-06-09
Hi! Just bought a MSI Wind U100 with these specs:

CPU: Intel Atom N270 1.6GHz
Chipset: Intel 945GME
RAM: 2GB, 1 + 1
HDD: 160GB 5400rpm
Wifi: RT2860, Bluetooth
6CELL Battery.

It had windows XP sp 3 installed on it. With Windows I got about 4.30 hours of work time with firefox, messenger and mIRC opened. 2 Days ago I installed Ubuntu 9.04 on it and deleted windows. Thats when the problems began -) First of all I can get a maximum of 3 Hours of worktime with nothing running on it ... weird :) Everything is extremely slow. Opening windows, closing them, changing tabs in everything etc.

When I open Audacious to play music the CPU is used about 40% all the time and I can't open anything else. Even disabling Compiz didn't do anything. Everything is in slow mode :)

Minimizeing tabs and Alt+Tab are slow like I'm on a PI CPU With 8MBs of ram ;)


First I downgraded from X intel driver 2.6.3 to 2.4. Things began to go better but not quite. Even when idleing the CPI is about 10% used.

I installed powertop and I can see that this "uhci_hcd:usb4" is responsible for about 50% of CPU wake ups so I guess that's the power drainer. Also typing this text is pain in the *** cos' its like I'm a faster typeer then the netbook is >) Its silly I mean and its pissing me off 

Here is lspci -vv : [http://vmetni.com/7hbjvn-3181?raw](http://vmetni.com/7hbjvn-3181?raw)

lsusb -vv : [http://vmetni.com/74ninb-3182?raw](http://vmetni.com/74ninb-3182?raw)

kernel version : 2.6.28-11-generic

powertop output : [http://vmetni.com/90gihr-3183?raw](http://vmetni.com/90gihr-3183?raw)


Anyone can assist ? :)

Poi poi.

---

### Post by Aleks` on 2009-06-09
It started to freeze up if i leave it on ubuntu for about 1 hour.

HALP.

---

### Post by Aleks` on 2009-06-10
Just found out that its on IRQ7 which is default for printers and paralel port. However during boot-up I see that IRQ7 is givven to "USB Controler"... Anyone ?...

---

