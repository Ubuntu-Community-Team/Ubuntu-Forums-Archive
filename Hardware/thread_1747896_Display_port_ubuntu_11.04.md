---
title: "Display port ubuntu 11.04"
date: 2011-05-03
forum: Hardware
---

### Post by Pimmetje on 2011-05-03
Hi all,

For 2 months now i own a HP 2740p notebook. As i need a linux box for education i installed ubuntu 11.04 as dualboot with my windows 7. After some playing around i found most things to work quite good. USB Headset, Docking station. External screen (VGA) works fine.

Now the part i have trouble with. The screen on the display port gives strange colors (u can see the windows etc but the colors are incorrect. I tried some settings on the screen and with xrandr. Nothing seems to fix it. So i tried a other screen but still the same issu. As the bios screen is correct displayed on the screen i rull out any hardware issu's (like the display port to HDMI converter) also because of the fact that the screens work under windows. 

If needed i can add a picture of the screen (it just has too much green & red and only a little blue). 


Maybe it will help 

**$ lspci**
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
43:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
44:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
44:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Does anyone know how to fix it or is it a driver issue that needs to be resolved?

In all cases thanks for reading,

Pimmetje

PS. Please post if u have questions i did not answered about the issue.

---

### Post by Pimmetje on 2011-05-06
Kind of bump.

Can i report this as a bug somewhere? Or is it no bug :D

I also added some pictures.

---

### Post by bevangg on 2011-05-17
Hi all
I have a similar problem, I have attached screenshots. I use a HP 8740w and when running windows 7 the external display (a toshiba lcd tv) colours are wrong, reds are displayed green and blues become red. When running ubuntu 11.04 it works fine. I am also using a displayport to hdmi adapter but surely that would not cause this.
Any ideas?

---

### Post by Pimmetje on 2011-05-17
I think it's a other problem as your problem is on Windows 7 and my problem is on Ubuntu. 

Anyway. Try updating your drivers in windows 7. If ur at latest version look if u can find a older version.

---

### Post by bevangg on 2011-05-17
Hi thanks for the reply. From the symptoms I suspected it may be a driver issue and installed todays beta from nvidia. This has resolved the problem and I hope this info may be at least of some use to you.

---

