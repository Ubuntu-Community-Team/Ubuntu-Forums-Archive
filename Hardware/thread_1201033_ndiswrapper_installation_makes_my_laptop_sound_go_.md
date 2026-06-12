---
title: "ndiswrapper installation makes my laptop sound go out"
date: 2009-06-30
forum: Hardware
---

### Post by njddjn on 2009-06-30
I installed ndiswrapper and got my WPN111 wireless adapter to work but after reboot Ubuntu would not load and one of the lines said "ALSA unloading... OK"  

I have reinstalled Ubuntu twice now to reset everything.  

here are my components:

```
noah@noah-laptop:~$ lsusb
Bus 001 Device 004: ID 1385:5f00 Netgear, Inc WPN111 RangeMax(TM) Wireless USB 2.0 Adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
noah@noah-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:08.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:08.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)

```

---

