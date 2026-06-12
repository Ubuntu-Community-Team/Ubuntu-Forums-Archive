---
title: "General USB weirdness on thinkpad"
date: 2011-01-08
forum: Hardware
---

### Post by fa2k on 2011-01-08
Hi, (this is probably a longshot....)

I have a Thinkpad T410i. I think there is something wrong with its USB controllers..

My USB sound card works, but I can't record while playing back audio. It works fine on another computer with Ubuntu 10.10. (there are some finer details about how it works on the thinkpad, the mic input completely goes away after 15min-1hour)

My TV card dies after a few minutes when I connect it to the thinkpad. It works fine in Windows on the same machine. It works fine on a different machine in Ubuntu. The other computer can also "revive" the TV card after it has been connected to the thinkpad. This is not possible with the thinkpad in windows mode, if it is in "dead mode", it is found as "Unknown device" :confused:

My USB keyboard, webcam, mouse and storage devices all work perfectly. It doesn't seem to make a difference if i connect the devices to a USB hub or to the laptop itself. 

sound card is 
```
0b05:1743 ASUSTek Computer, Inc. Xonar U1 Audio Station
```
TV card is "TerraTec Cinergy Hybrid T XS" (I can't be bothered to revive it & get the USB ID, probably doesn't make a difference)


I reckon it must be a combination of a software and a hardware issue.
Here is lspci, and then lspci -v for just the USB controller
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
0d:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```
```
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 2163
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2428000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

```
Any ideas, or anyone having the same problems?

Thanks

Edit:
I forgot to say, I had a USB SoundBlaster card that suddenly stopped working (that may be related). Also there are sometimes some small sparks when touching the outer part of a USB or DisplayPort cable to the corresponding port (before inserting it).

---

