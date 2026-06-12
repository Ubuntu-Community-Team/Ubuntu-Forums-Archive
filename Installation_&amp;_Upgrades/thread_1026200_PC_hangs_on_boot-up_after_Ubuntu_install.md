---
title: "PC hangs on boot-up after Ubuntu install"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Jotun on 2008-12-30
I have Windows XP and tried install Ubuntu 8.10 from within Windows. I then allowed it to reboot my system, but it won't boot. I'm not sure what to call it, but it is the very first thing that appears when I boot my PC. I suppose you could call it the BIOS screen, where it simply says:

-----------------------------------------------------------

Phoenix - AwardBIOS v6.00PG
Copyright (C) 1984-2003, Phoenix Technologies, LTD

(6A61ITT2) Release number 691N0P31
NVIDIA BIOS Version: 2.053.A1
Main Processor : Intel(R) Core(TM)2 CPU 528MHx(88x6.0)

[space where it is supposed to detect drives, but it doesn't, it simply stays blank]

Press DEL to enter SETUP, ESC to Enter Boot Menu
09/28/2007-122-CK-NF68-6A61ITT2C-00

-----------------------------------------------------------
Not only will it not detect any drives whatsoever, but I cannot enter the CMOS nor the boot menu. I have tried using a USB keyboard and a PS/2 keyboard and it will not respond to either one.

UPDATE: After letting it sit at this screen for about 10 minutes, it finally populated the blank area with my optical and hard drives, but it gave me this message at the bottom:

"Warning! Now System is in Safe Mode.
Please reset CPU or Memory Frequency in the CMOS setup

Press F1 to continue, DEL to enter SETUP".

This is strange because I have never attempted to overclock my CPU. My PC was working just fine before all this, so I think it must've been something that went wrong with the Ubuntu install.

Okay, so I went into the CMOS and reset everything and then reboot. It still hangs for a long time and takes forever to populate the area where it is supposed to detect the drives.

This is my PC's setup:
MOBO: EVGA nForce680i
CPU: Intel Core 2 Duo E8500 Wolfdale 3.16GHz
RAM: G.SKILL 1GB DDR2 SDRAM DDR2 1066 (x4, total 4GB)
GPU: BFG Tech GeForce GTX 280
PSU: ZALMAN ZM850-HP 850W
HDD: Seagate Barracuda 80GB SATA (primary C: drive)
HDD: Western Digitial Caviar Green 1TB (secondary I: drive)

I also have two optical drives, both of them LG GH22NP20, that occupy letters D: and E:, and two virtual drives that occupy F: and G:

I just finished entering my CMOS and set the CPU clock speed to the minimum multiplier of 6x and it still hangs for a very long time on the BIOS screen, but it always eventually populates the area and boots. I can now boot into WinXP or Ubuntu, but it still hangs for a very long time each time I boot up. Any and all help is appreciate in advance.

---

### Post by abn91c on 2008-12-30
> **Jotun said:**
> I have Windows XP and tried install Ubuntu 8.10 from within Windows. I then allowed it to reboot my system, but it won't boot. I'm not sure what to call it, but it is the very first thing that appears when I boot my PC. I suppose you could call it the BIOS screen, where it simply says:

-----------------------------------------------------------

Phoenix - AwardBIOS v6.00PG
Copyright (C) 1984-2003, Phoenix Technologies, LTD

(6A61ITT2) Release number 691N0P31
NVIDIA BIOS Version: 2.053.A1
Main Processor : Intel(R) Core(TM)2 CPU 528MHx(88x6.0)

[space where it is supposed to detect drives, but it doesn't, it simply stays blank]

Press DEL to enter SETUP, ESC to Enter Boot Menu
09/28/2007-122-CK-NF68-6A61ITT2C-00

-----------------------------------------------------------
Not only will it not detect any drives whatsoever, but I cannot enter the CMOS nor the boot menu. I have tried using a USB keyboard and a PS/2 keyboard and it will not respond to either one.

UPDATE: After letting it sit at this screen for about 10 minutes, it finally populated the blank area with my optical and hard drives, but it gave me this message at the bottom:

"Warning! Now System is in Safe Mode.
Please reset CPU or Memory Frequency in the CMOS setup

Press F1 to continue, DEL to enter SETUP".

This is strange because I have never attempted to overclock my CPU. My PC was working just fine before all this, so I think it must've been something that went wrong with the Ubuntu install.

Okay, so I went into the CMOS and reset everything and then reboot. It still hangs for a long time and takes forever to populate the area where it is supposed to detect the drives.

This is my PC's setup:
MOBO: EVGA nForce680i
CPU: Intel Core 2 Duo E8500 Wolfdale 3.16GHz
RAM: G.SKILL 1GB DDR2 SDRAM DDR2 1066 (x4, total 4GB)
GPU: BFG Tech GeForce GTX 280
PSU: ZALMAN ZM850-HP 850W
HDD: Seagate Barracuda 80GB SATA (primary C: drive)
HDD: Western Digitial Caviar Green 1TB (secondary I: drive)

I also have two optical drives, both of them LG GH22NP20, that occupy letters D: and E:, and two virtual drives that occupy F: and G:

I just finished entering my CMOS and set the CPU clock speed to the minimum multiplier of 6x and it still hangs for a very long time on the BIOS screen, but it always eventually populates the area and boots. I can now boot into WinXP or Ubuntu, but it still hangs for a very long time each time I boot up. Any and all help is appreciate in advance.

google your motherboard manual, then remove the cmos battery to reset the bios to factory settings, you may need to remove a board jumper also, look in the manual for that. Also it may be possible the battery is almost dead.

---

### Post by Jotun on 2008-12-30
Still hangs after taking battery out and putting it back in and resetting CMOS. I'm thinking I might have to replace my RAM. Strange that this problem would show up after installing Ubuntu though.

---

