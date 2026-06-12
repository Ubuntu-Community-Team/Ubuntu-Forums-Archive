---
title: "M3A79-T Deluxe"
date: 2008-12-10
forum: Hardware
---

### Post by Ridor on 2008-12-10
I just got an Asus M3A79-T Deluxe motherboard, and while my trusty slackware install boots up fine, the ide hard drive it is on is realy slow:
/dev/hda:
Timing buffer-cache reads: 128 MB in 0.11 seconds =1120.07 MB/sec
Timing buffered disk reads: 64 MB in 46.92 seconds = 1.36 MB/sec
the sata drive I store suff on is:
/dev/sda:
Timing buffer-cache reads: 128 MB in 0.12 seconds =1100.60 MB/sec
Timing buffered disk reads: 64 MB in 1.09 seconds = 58.57 MB/sec.
Lspci gives me this:
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e
_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0
port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gp
p port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gp
p port D)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI
mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0605 (rev a
2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit
Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
(rev b2)
04:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70).
I compile my own kernel with slackware on my desktop (my laptops run ubuntu) and I don't know what driver to use. Would Ubuntu 8.04 run well on this?
Also, I've tried the Ad1889 driver for the audio (adi2000b device) and that hasn't worked yet.
Thanks in advance for your help.

---

