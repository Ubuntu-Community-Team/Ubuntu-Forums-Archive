---
title: "changing my external monitor to primary monitor...but its a lot more complicated"
date: 2012-01-01
forum: Hardware
---

### Post by om23 on 2012-01-01
So I have a Dell Inspiron 1420. The screen got damaged to the point where I could only see a little part of the top left corner. Considering the costs I decided to use my tv as a external monitor. Then considering how fun and awesome it would be, I installed Ubuntu 10.10 and removed Windows off the laptop. So at this point, I had the laptop hooked up to the TV via S-video and audio through a cable that converted the microphone wire to red & white component wires. I was using a wireless keyboard and mouse and its been pretty fun. Two weeks ago I decided to buy a projector. The setup is running extremely well. I also decided to completely remove the original laptop display (its fun carrying the laptop part around- parents were shocked lol). 
But here is the problem (I've had it since the tv): even though ubuntu recognizes the projector as the external display, if I switch to watch some tv on the projector (actual live channels) and return back to the laptop (simply unplugging s-video wires) after an hour or so, the laptop no longer recognizes the external monitor. The external monitor is mirrored as the default (its the only monitor found- since its the only one connected). 
I was thinking if I somehow changed the s-video input (projector) then the laptop should recognize the project as the original monitor? Would it be possible to go into the bios (or somewhere) to change what monitor the laptop recognizes every time it books even if I am not using ubuntu?
I want to install windows back onto the laptop (then try Windows 8 ) but I'm afraid that the laptop won't recognize the projector as the monitor since the projector is still an external display and all. I know this is probably confusing/frustrating/challenging but I am still pretty new to Ubuntu and might only have one shot at fixing the problem.
Please help, and if you have any questions, ask! 
Thanks!

---

### Post by Haneef Mubarak on 2012-01-01
What graphics do you have? If you don't know, run this in a terminal and post the output:
```
sudo lspci
```

---

### Post by om23 on 2012-01-01
> **Haneef Mubarak said:**
> What graphics do you have? If you don't know, run this in a terminal and post the output:
```
sudo lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Mark Phelps on 2012-01-02
Would advise against trying Windows 8 -- at least, at this time.

It's an alpha.  Not only does it have serious problems, it's also due to be replaced sometime in February with the Beta.

I would hold off until the Beta is available.  That will be quite different from the Alpha currently available.

---

### Post by om23 on 2012-01-02
I'll probably wait for the Beta to come out then. Thanks.

One more thing: When I updated to Ubuntu 11.10 the external display no longer worked (when I still had the original display attached). It might have been due to missing drivers or whatnot. But I'm not risking anything until I get this resolved. Basically I want to use this for testing and so on.

---

### Post by om23 on 2012-01-04
Can anyone point me in a particular direction because I have no clue what to do...........

---

