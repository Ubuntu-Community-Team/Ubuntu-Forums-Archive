---
title: "Netgear WG511 not recognised"
date: 2011-12-03
forum: Hardware
---

### Post by psionman on 2011-12-03
I'm running Ubuntu 10.4.3 on an old Dell Inspiron. I'm trying to get on the net and need to use a Netgear WG511 card. Ubuntu does not seem to recognise it (it works fine with windows and Puppy)

The command

```
lspci -nn
```

produces the following output

> jeff@jeff-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]
07:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)



I can't see the WG511 in there

As a newbie, can someone please help?

---

### Post by psionman on 2011-12-04
This now solved thanks

Got a fast response on LinuxQuestions.org:rolleyes:

---

