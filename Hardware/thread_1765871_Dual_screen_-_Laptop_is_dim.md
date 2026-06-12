---
title: "Dual screen - Laptop is dim"
date: 2011-05-23
forum: Hardware
---

### Post by pafindr on 2011-05-23
I'm having issues with dual screens on my brother's laptop. I would appreciate any help.
His computer is a 
Gateway NV78
Intel Corporation Mobile 4 series chipset integrated graphics controller. 
Dual boot for Win 7 and Ubuntu 11.04

We did a fresh install of Ubuntu 11.04 from CD and now the laptop monitor is really dark (you need a flashlight to see things) but the external monitor is fine. The external monitor is connected via the VGA port.
Both monitors work fine when in Windows.
I tried editing the grub menu by pressing "E" and changing from "quiet splash vt.handoff=7" to "quiet splash acpi_osi=" but all that did was not recognize dual monitor (only the external monitor worked).

I know very little about the workings of Ubuntu (enough to get myself in trouble) so if you can dumb it down a little it would be really helpful :) 

Again I would greatly appreciate any help!

---

### Post by trozamon on 2011-05-23
The only thing I can think of is try going to power management and checking what you have the screen brightness set to.

---

### Post by pafindr on 2011-05-24
Ok, under power management I changed settings in AC Power to Never for sleep and Never for inactive, I set display brightness to 100%. In batter power I set it to Never for sleep, I unchecked the box for Reduce backlight Brightness, and unchecked for Dim display when idle.

These didn't help :(  Any ideas?

Thanks

---

### Post by trozamon on 2011-05-25
The only other thing I can think of at the moment is checking the display settings in the BIOS, if your laptop has them. I know Windows works correctly, but just check anyway. I'll do some looking.

---

### Post by pafindr on 2011-05-25
Doesn't changing the "quiet splash" to "acpi_osi=" change the BIOS setting?

I'll take a look at the BIOS and see what it does.

EDIT***
Ok, I checked in BIOS but there wasn't anything I could find on backlight settings.

---

### Post by yalejatt on 2011-05-25
Hello, I am also having backlight problems:
Long story short - I have an HP laptop with a NVidia 9300 GS card, running 64-bit Windows 7. I installed Ubuntu 11.04 64-bit to a 60 GB partition. The fn keys worked at this time, to control the brightness. I used Ubuntu for a few days, and I installed some updates, which I think included a NVidia driver. The next day, I turned on my pc and the screen was so dark, I had to use a flashlight to see what was on the screen. I uninstalled Ubuntu by deleting the partition in Windows, which caused the computer not to boot. Finally, by using the Ubuntu cd, I saved my files, wiped my system, and now run only Windows 7. The screen is still unbearably dark, it seems that the backlight isn't working. I already tried reinstalling the drivers in Windows, I tried changing the brightness in the power options, and I already tried the fn brightness keys, which used to work. Also, when I plug into a VGA monitor, the image has normal brightness. What can I do?:confused:

---

