---
title: "HP nx7300 ACPI question (suspend/hibernate)"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by taragui on 2007-02-04
Hi. I had a happy first Ubuntu installation using Edgy yesterday on my new HP nx7300. I was impressed by the installer (I'm a Linux old-timer and used to Debian, which means the difference was readily noticeable), and most of the stuff worked out of the box (haven't tested ieee1394, modem or CardBus, though).

I had some tweaking to do in order to get the Broadcomm 4311 WiFi card running, but compiling a recent version of ndiswrappers and grabbing the Windows driver worked just fine. The only important thing that seems missing is support for hibernation/suspend to RAM; trying to do either lands me with a blank screen and some disk activity that won't go away until I turn the laptop off and then on again.

Now, HP markets a number of different setups under this name, so browsing the little I could find on this model on the net was not very useful. I gather it may have to do with the SATA controller, which would explain the continued disk activity. In any case, I'm posting the output of lspci to double check. In anyone has had experience with this controller, I'd be grateful for pointers. I'm not afraid to recompile whatever might be needed; I'm just a newbie when it comes to laptop hardware.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
02:06.0 CardBus bridge: Texas Instruments Unknown device 8039
02:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

Thanks in advance,

taragui

---

### Post by capdog on 2007-02-07
Hi taragui, I have also just installed Ubuntu 6.10 on my NX7300, but I suspect it's a different model. Mine is the RH700EA, with Core 2 Duo 1.83G, 120h HD, Intel Pro/Wireless 3945 abg.

My suspend also doesn't work properly... :(

The cpu stepping works but it doesn't get past the 1,33 GHz level up to 1.83. 

Otherwise it seems ok! Apparently there is something called a "bad state" that the BIOS gets into, and affects many subsystems... Google it, it's caused by the PS2 driver or something. I'm trying to fix now, will post results.

---

