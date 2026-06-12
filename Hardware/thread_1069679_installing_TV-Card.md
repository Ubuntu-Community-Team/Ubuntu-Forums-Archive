---
title: "installing TV-Card"
date: 2009-02-14
forum: Hardware
---

### Post by aeltester on 2009-02-14
Hey guys,

I'm trying to get my old pinnacle TV-Card to work.

lspci:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)

```

dmesg:
```

$ dmesg | grep bttv
[   13.130170] bttv: driver version 0.9.17 loaded
[   13.130172] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.130216] bttv: Bt8xx card found (0).
[   13.130225] bttv 0000:05:02.0: can't derive routing for PCI INT ?
[   13.130226] bttv 0000:05:02.0: PCI INT ?: no GSI
[   13.130235] bttv0: Bt878 (rev 17) at 0000:05:02.0, irq: 255, latency: 32, mmio: 0xe0000000
[   13.130492] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   13.130494] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   13.130497] bttv0: can't get IRQ 255
[   13.130513] bttv: probe of 0000:05:02.0 failed with error -22

```

zapping says it can't find /dev/video0.
tvtime just doesn't give me any option for the input.

what can I do?

thanks in advance

:P

---

