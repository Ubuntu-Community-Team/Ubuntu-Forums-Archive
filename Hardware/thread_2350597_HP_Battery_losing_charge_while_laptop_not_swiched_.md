---
title: "HP Battery losing charge while laptop not swiched on"
date: 2017-01-25
forum: Hardware
---

### Post by Hachi-Roku on 2017-01-25
Hey all,

Bit of a weird one. My few month old HP 250 laptop runs dual boot Win10 and Ubuntu studio latest version.

When the laptop is SWITCHED OFF it loses roughly 85% battery power in 3 days.  Nothing external is left connected, literally just sitting there.

The battery checks on the inbuilt bios testing passes fine. Updated the bios as HP suggested. HP tell me that the clock and date need power to keep them current.... seems to me thats a big freakin' clock.

I've ran dual boots for years and never had this problem before. I've never had ubuntu studio before, is there something specific about the studio build that could cause this?

Anyone suffered this power injustice before???

Thanks for reading.

---

### Post by MartyBuntu on 2017-01-25
> **Hachi-Roku said:**
> 
Anyone suffered this power injustice before???



Yes, this is an HP WOL (Wake On Lan) problem that is well documented. You're not crazy.
You need to switch off WOL in both Windows and Ubuntu.

---

### Post by Hachi-Roku on 2017-01-26
Thanks for the fast reply Marty. Love the Ubuntu community :).

It was already switched off in win10 and there seems to be nothing about it in the BIOS (which i found odd). Although im rechecking because wol seems to hide behind other names sometimes.

I check in my Ubuntu and sure enough it was switched on. I set it to disable and we will see if it does the trick over the next few days.
I'll hit back with a status in a few days in case it's helpful to anyone else who comes across this thread.

For those playing at home i did this to check;
```
sudo ethtool eth0
```
search for wol line in the output, if it's not "d", then do this;
```
sudo ethtool eth0 -s wol d
```
then check it stores the "d" value in the wol line after a reboot.

---

### Post by MartyBuntu on 2017-01-26
You probably need to make this a persistent change. It seems that system updates on the network stack re-activate WOL.
I haven't had muchluck with that...I just occasionally check WOL and disable it if it's on.

---

