---
title: "Gateway 4530 gz Audio not working Fiesty"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by anil_chin on 2007-11-17
i have a Gateway 4530gz, which is similar to most gateway 4000 series laptops. I am unable to listen to any sound in the laptop. Some information from my laptop

$ sudo lspci -v | grep -i -A 5 audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]

$cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at 0xe0100c00, irq 10

$  cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

I just want to use skype and play some music files.

---

