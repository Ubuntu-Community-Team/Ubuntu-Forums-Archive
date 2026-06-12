---
title: "Missing CD and DVD players"
date: 2009-05-19
forum: Hardware
---

### Post by dargaud on 2009-05-19
Hello all,
I've been using KUbuntu for a few months with few problems and only now did I try to read a CDrom... without success. 
[LIST]
[*]When I insert a USB key, it pops a dolphin window after confirmation, but nothing happens with a CD inserted in either drive.
[*]I see /media/cdrom0 and 1 but both are empty.
[*]There doesn't seem to be anything related to cd drives in dmesg.
[*]fdisk -l doesn't show any CDs.
[*]No mention in /etc/fstab either
[*]K3b tells me I don't have any CD recorder.
[/LIST]
I can boot from a CD so the drives DO work.
For what it's worth those IDE drives are connected not to the motherboard but to a PCI board: Promise Technology, Ultra133 TX2.
I don't know if this is related but I have tons of dmesg errors:
```
[366307.569836] sd 9:0:0:0: [sdh] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[366307.569838] end_request: I/O error, dev sdh, sector 12679616
[366307.569865] Buffer I/O error on device sdh1, logical block 1032
[366307.569867] lost page write due to I/O error on sdh1

```
Any suggestions ?
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

---

### Post by dargaud on 2009-09-10
I'm going through my past messages and I forgot to post a resolution to that one: the PCI to IDE controller card wasn't seated properly: it would work fine just plugged in during tests, but as soon as I tightened the screw and closed to box it would fail.

---

