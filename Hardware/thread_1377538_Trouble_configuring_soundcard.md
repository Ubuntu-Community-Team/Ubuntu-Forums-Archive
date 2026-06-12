---
title: "Trouble configuring soundcard"
date: 2010-01-10
forum: Hardware
---

### Post by gusteman on 2010-01-10
Hi there all you Ubuntu lovers!
I recently upgraded my PC with a new (sic) motherboard which I got from my brother-in-law. For the time being I am running Hardy but can't seem to find the right soundcard to configure. Could anyone please help me on this?
Hereafter I placed the summary of the motherboard according to the manufacturer.
Thanks in advance.


[I]Chipset Intel 865PE + ICH5
Processor Socket 478 on board.
Supporting P4 CPU
(including Prescott CPU and Hyper Threading Technology).

Front Side Bus 800/533/400MHz Front Side Bus.
Memory 4 x 184-pin DDR DIMM Sockets.

Supporting unregistered non-ECC DDR 400/333/266 DRAM up to 4GB.

Supporting Dual-Channel.


Expansion Slots 1 x AGP 8X/4X Slot.

6 x PCI Slots.

On-Board EIDE 2 x ATA100/66/33 IDE connectors supporting up to 4 IDE devices.
On-Board SATA 2 x Serial ATA connectors supporting 2 Serial ATA HDDs. (by ICH5)

Integrated Super I/O 1 x Floppy Port.

1 x PS/2 Mouse Port.

1 x PS/2 Keyboard Port.

1 x LAN Port. (For SL-86SPE-L only)

1 x Parallel Port.

2 x Serial Ports.

8 x USB 2.0/1.1 Ports. (2 integrated, 6 via optional cables)

Audio Ports.

RAID --
IEEE1394 --
Audio 6-Channel AC'97 Audio.
LAN 10/100 LAN Function. (For SL-86SPE-L only)
BIOS AMI BIOS.

Flash Memory for easy upgrade.

Form Factor ATX Form Factor (305mm x 244mm)
Other Features BIOS FSB Setting.

BIOS Writing Protection.

BIOS AGP, DIMM Voltage Setting.

BIOS Multiplier Setting.

SmartDoc. Anti-burning Shield. (optional)

RedStorm2 Overclocking Technology. (optional)

H/M Monitor.

STR Function. (optional)


CPU Support
Compatibility

RAM Memory Support
Compatibility
[/I]

Greetings, Gusteman


Stupid me:
when configuring the bios I overlooked the southbridge and northbridge settings.
When I went to look into them I found that the soundcard was "disabled".
Enabling it solved the problem!!
Sorry guys!

---

