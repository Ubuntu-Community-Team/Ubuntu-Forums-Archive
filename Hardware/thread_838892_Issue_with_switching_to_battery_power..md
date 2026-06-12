---
title: "Issue with switching to battery power."
date: 2008-06-23
forum: Hardware
---

### Post by WonderBread on 2008-06-23
I have a problem with my Thinkpad R51 (specs included at the end of the post) with Ubuntu 8.04 that when I unplug the AC adaptor and switch to battery, after about three seconds of being on battery, Ubuntu does a hard restart of the laptop (does not shut down), and until it is plugged back it continues to do this on the loading screen.

I did not have this problem with 6.06 (everything ran fine), and have applied all updates to 8.04. I am new to linux, although I have been working with Windows boxes for the most part of a decade. I really have no idea where to start looking to find the problem, nor do I have any clue what it could be. Someone suggested trying to boot Ubuntu with acpi=force, but that did not help.

If anyone could offer any help, that'd be awesome.

> 
mlavoie@LapBox2:~$ lspci

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)

02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

mlavoie@LapBox2:~$ 


---

### Post by WonderBread on 2008-06-24
Bump :(

---

### Post by cwbar_1 on 2008-06-24
OK. I may be over my head in this but, have you checked System> Administration> Services? Make sure you have the 2 power management (acpid & apmd) services enabled.

---

### Post by WonderBread on 2008-06-24
> **cwbar_1 said:**
> OK. I may be over my head in this but, have you checked System> Administration> Services? Make sure you have the 2 power management (acpid & apmd) services enabled.

Both are enabled. It is weird, when I remove the power plug, the machine runs for about a second, and then drops to a boot screen. There is also NO mention of ANYTHING in any logs that I have looked in.

---

### Post by cwbar_1 on 2008-06-24
Try entering _dmesg_ in terminal.  Hopefully it will give you a starting point.

---

### Post by WonderBread on 2008-06-24
Already been suggested, but I can't find anything that would seem to be of help.

Of course, I'm not entirely sure what I should be looking for.

---

### Post by cwbar_1 on 2008-06-24
Bump, Anyone?

---

### Post by WonderBread on 2008-06-24
In perhaps the oddest thing possible, for some reason when I have the Folding@Home client running, the laptop DOES NOT perform the hard reboot, and functions normally... until I stop the client, and then it performs the reboot.

I am truely stumped now.

---

### Post by WonderBread on 2008-06-26
One last bump, I guess. :(

---

