---
title: "No sound through netbook speakers"
date: 2009-10-05
forum: Hardware
---

### Post by ylar34 on 2009-10-05
Hi, I am running Karmic Koala 9.10 beta on an ASUS eeepc 1000 and the sound that comes from the built in speakers decided to stop working. The headphone jack has sound but the built in speakers don't. This was an issue as well when I was running Jaunty Jackalope 9.04 and now it seems to be back. I have tried experimenting with various sound settings with no success. Any help is appreciated. Thanks.

---

### Post by ylar34 on 2009-10-05
here is my lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

---

### Post by MilchFlasche on 2009-10-12
Me too, running Kubuntu 9.10 beta on Eee PC 901, at first it can play sound, but after updating or some other reason both PulseAudio and Intel HDA Audio ceased working.

---

### Post by BenypX on 2009-10-12
Ubuntu Jackalope too... sound is messed up, I am dual booting and sound works in Windows 7 but doesn't work in ubuntu. Also, the sound works when i first open ubuntu, it makes the noises, but once in logged in... no sound

---

### Post by Brzydal on 2009-10-13
Same here on Karmic. lshw bring me this:
```
*-multimedia
             description: Audio device
             product: System Controller Hub (SCH Poulsbo) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:23 memory:f3f38000-f3f3bfff
```What to do? some 1 got any sugestions what check, or reinstall? alsa?

---

### Post by elfuego on 2009-11-14
I have the same problem here. Eeepc 901 / linux, fresh install of Ubuntu 9.10 and no sound out of internal speakers (line-out works fine). I find this funny, since they work on the Live edition from USB stick.

Did anyone have some luck in finding a solution yet?

---

