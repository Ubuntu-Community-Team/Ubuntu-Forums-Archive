---
title: "Toshiba built-in SD card reader issues"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Metacarpal on 2006-11-12
Hi all,

I'm running 6.10 on a Toshiba Tecra A5-S519 with a built-in SD card reader.  The card reader is listed in my device database, and the system is detecting the insertion of the card, but it is not mounting.

When I run dmesg in terminal after inserting the card, the last line is:
```
[17247878.596000] tifm_7xx1: sd card detected in socket 3
```

Nothing appears for the card reader in /dev/ or /media/

Attached is a screenshot of the entry in device manager.

Anybody know how I can access the card using my built-in reader?  Thanks in advance!

---

### Post by Younes on 2006-11-12
Try ```
lspci
``` at a terminal.

You should get something like

> 02:09.0 CardBus bridge: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments PCI7411,7421,7611,7621 Firewire Controller
[B][COLOR="Red"]02:09.3[/COLOR] Unknown mass storage controller: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 Flash Media Controller
02:09.4 Class 0805: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 SD Host Controller[/B]

The Flash Media Controller driver has been abandoned as far as I know (got as far as detecting insertion/removal I guess). But the SD Host Controller driver is known to work. On TI chips only one controller can be active, and it's probably the Flash Media controller, so you have to disable it.

To disable it first get the current value and write it down

```
setpci -s [COLOR="Red"]02:09.3[/COLOR] 4c
```

then set the 2nd bit of that register as follows

> setpci -s [COLOR="Red"]02:09.3[/COLOR] 4c=2:2

Reboot if necessary.

Unfortunately my Toshiba has a Toshiba SD controller, so I don't know if the above will work, but it works for others. If it does work you will have to set that 2nd bit every time you reboot, since the Toshiba firmware by default enabled the TI controller. I suggest running it in a script at startup.

And finally, don't forget to let me know if it works!

---

### Post by Metacarpal on 2006-11-12
> **Younes said:**
> Try ```
lspci
``` at a terminal.

You should get something like



The Flash Media Controller driver has been abandoned as far as I know (got as far as detecting insertion/removal I guess). But the SD Host Controller driver is known to work. On TI chips only one controller can be active, and it's probably the Flash Media controller, so you have to disable it.

To disable it first get the current value and write it down

```
setpci -s [COLOR="Red"]02:09.3[/COLOR] 4c
```

then set the 2nd bit of that register as follows



Reboot if necessary.

Unfortunately my Toshiba has a Toshiba SD controller, so I don't know if the above will work, but it works for others. If it does work you will have to set that 2nd bit every time you reboot, since the Toshiba firmware by default enabled the TI controller. I suggest running it in a script at startup.

And finally, don't forget to let me know if it works!

Thanks for replying!  I tried the above, and here's what I got:

From lspci:```
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
```
```
metacarpal@musecatcher:~$ setpci -s 06:04.3 4c
ff
metacarpal@musecatcher:~$ setpci -s 06:04.3 4c=2:2
pcilib: Cannot open /sys/bus/pci/devices/0000:06:04.3/config

```

I'm guessing that means it didn't work.  I noticed though, that it didn't list the flash controller as "unknown"...

---

### Post by Younes on 2006-11-12
It looks like you have a slightly different setup. You're using the 7xx1 driver, which is different from the Flash Media driver I was thinking about and supposedly works according to the author.

Insert the card and try mounting it yourself. I have no idea where it would appear in /dev or what the args to mount would be though, sorry.

---

### Post by dog mad on 2006-11-15
I found a solution for my Sattelite P100 with the same TI (Texas Instruments ) drivers as you have. It is outlined on [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo#head-1d524a1bbe9634283a733cec4e3d1cf57684079a](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo#head-1d524a1bbe9634283a733cec4e3d1cf57684079a)

I am enjoying this software. I was a unix head until 87 when I had to go windows as that was what I was given. It has now got to the point where more of what I want is available in Linux than in Windows. (Maths/Elecronics).
Good stuff. Hope one day I can be useful

---

### Post by Timokl on 2006-12-21
> **Younes said:**
> Insert the card and try mounting it yourself. I have no idea where it would appear in /dev or what the args to mount would be though, sorry.

I found this page which gives you an idea how to mount a memory stick by hand: [http://www.linuxforums.org/forum/peripherals-hardware/24239-usb-memory-stick-doesnt-work-ubuntu.html]("http://www.linuxforums.org/forum/peripherals-hardware/24239-usb-memory-stick-doesnt-work-ubuntu.html")

---

