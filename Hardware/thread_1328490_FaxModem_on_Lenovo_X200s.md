---
title: "Fax/Modem on Lenovo X200s"
date: 2009-11-16
forum: Hardware
---

### Post by realn on 2009-11-16
Please, has someone made it work?
I don't even know for sure what is the device for the modem, the scanModem tool is somehow confused:


A candidate modem is not evident among the PCI devices:
------------------------------------------------
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

I tried to use the smartlink + slamr packages, it seems I can connect through minicom to a modem devize, I can send commands, but evrytime I want to dial (ATDT commands) a number I get NO CARRIER ERROR message.
 
 I am not even sure what the problem is, can someone who DID IT tell me HOW she/he did it?

 Thank you so much.

---

### Post by realn on 2009-11-17
Please, there's no one who solved this issue? Should I dump ubuntu and install M$ only for that?

---

