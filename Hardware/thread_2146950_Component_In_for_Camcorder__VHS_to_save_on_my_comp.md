---
title: "Component In for Camcorder / VHS to save on my computer"
date: 2013-05-20
forum: Hardware
---

### Post by flipjarg on 2013-05-20
I am trying to get my component inputs to work but have failed with each thing I try. I've tried TVtime and it just says no signal. When I try mplayer for /dev/video0 it is just a black screen with a tiny bit of static. It looks the same whether something is plugged in or not. Also, ivtv is installed but maybe things aren't configured correctly. I don't know. Also `cat /dev/video0 > test.mpg` just produces a black screen with white noise. Can anyone help point me in the right direction?

lspci
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
**02:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)**
02:05.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem
02:08.0 Ethernet controller: Intel Corporation NM10/ICH7 Family LAN Controller (rev 01)

```

---

