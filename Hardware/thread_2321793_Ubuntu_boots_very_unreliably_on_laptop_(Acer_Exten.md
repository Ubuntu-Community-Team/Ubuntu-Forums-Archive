---
title: "Ubuntu boots very unreliably on laptop (Acer Extensa 2509)"
date: 2016-04-24
forum: Hardware
---

### Post by Megadoomer on 2016-04-24
Hello everyone,

after using Ubuntu 12.04 for years, I decided to upgrade my laptop, which is an Acer Extensa 2509 model, to 16.04.

I downloaded the ISO from the official webseite and tried both installing it via DVD and USB drive. I had trouble booting the live system, because the boot would suddenly freeze at the splash screen with the CPU-fan turning on at full speed and off again in intervals of 10 (on) and 20 (off) seconds. This would go on endlessly, I've left the laptop on for a few hours and still nothing would happen besides the fan spinning periodically.

Eventually, I managed to boot the live system (without changing any BIOS or other system settings, apparently by chance) and was able to install Ubuntu. The live system worked without a problem, I was able to format the internal drive, set up partitions and start the installation. After a reboot, the system started normally, the splash screen was shown as usual and I was able to log into the system. All other system functionality appeared to work normally as well. After three or four reboots, the laptop again started to freeze at the splash screen for unforseeable reasons (again, no changes to the BIOS or other system properties, no update was installed immediately before this occured).

The MD5 checksum of the ISO I used to install the system is identical to the one supplied on the official website. So far, I've tried to install in Legacy BIOS and UEFI modes, on gpt and mbr partitioned drives with LVM partitions and without. I also tried to install 14.04 and 15.10, as well as the Xubuntu and Lubuntu variants, but the problem persists (possibly also in other releases). The only way I am able to reliably boot the system is with Ubuntu 12.04, while the splash screen is not displayed correctly in this version, it never froze while I was using it.

I definitely need help with this issue, as I am unsure what could cause this or what can be tried to solve it. Currently, there is a successful UEFI installation of Ubuntu 16.04 on the drive with almost no changes to the settings. It usually needs a couple of tries before the system starts, but I am generally able to boot it. If there are any suggestions that you have on what I can do to make the system boot more reliably or analyse the problem, please let me know. It would also be no problem to break this system, as I can just reinstall it, should that happen.


Best regards.


These are the system specifications:

Acer Extensa 2509
Intel Pentium N3530 CPU
Intel HD Graphics Bay Trail IGP
4 GB DDR3 RAM
256 GB SSD

---

### Post by weatherman2 on 2016-04-24
Ubuntu 16.04 is still really new - released just a few days ago.  I would personally not switch to it right away unless you have some pressing need to do so, especially if you have strange issues..  Why not upgrade to 14.04 instead?

---

### Post by Megadoomer on 2016-04-25
Hi weatherman2,

as I wrote in my initial post, 14.04 has exactly the same problem. The only system that worked reliably so far was 12.04, which only has almost a year of support left and I would like to try figuring this out before I'll be in trouble or in need of yet another laptop.

---

