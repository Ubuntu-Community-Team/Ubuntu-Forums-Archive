---
title: "D-Link AirPlusG DWL-G630 E2 installing problem"
date: 2008-04-25
forum: Hardware
---

### Post by groadin on 2008-04-25
Hi, is there anybody who has this card (note that I mean E2 version card, which has rt61 chipset)? I would like to know that anybody managed it to run on Ubuntu.

I tried several ways:

1) With native drivers in Ubuntu 7.10 32bit, it says (after insertion or during boot in logs):
> 
rt61pci_init_eeprom : Error - Invalid er chipset detected
rt2x00lib_probe_dev : Error - failed to allocate device

And nothing happens (no freeze, but card doesnt work).

2) With rt61 CVS from serialmonkey it says something like this:
> 
could not load firmware (is a driver installed?)
// freeze

I tried to put firmware files to /lib/firmware/[kernel]/, and even to /lib/module/extra/ where rt61.ko is.

3) With XP driver by ndiswrapper, system freeze after loading this driver. Sometimes it displays starting ndiswrapper info up to "wlan0 interface created" etc (with info about supported encryptions), and next it freeze, sometimes it freezes even before wlan0 creation info.

The card itself is working in 100% under XP, so it cant be broken. Please post replies what should I check, and especially if there is anybody with E2 version of this card, please help / post results of your fight :-).

---

