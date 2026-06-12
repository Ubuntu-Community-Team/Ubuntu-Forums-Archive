---
title: "Thinkpad X30 Cardbus/PCMCIA/CompactFlash not recognized"
date: 2008-09-30
forum: Hardware
---

### Post by Caimlas on 2008-09-30
I'm running kubuntu/ubuntu 8.04, fully apt-get upgraded, on an IBM Thinkpad x30. This laptop has a  Ricoh Co Ltd RL5c476 II (rev a8) Cardbus bridge; there are two ports, one for CF devices and the other for PCMCIA/Cardbus devices. There is also a Ricoh FireWire port, but I've yet to try using it (no FireWire devices).

However, when I insert either CF or PCMCIA/Cardbus devices (and I've tried nearly a dozen) they are not recognized by the kernel and show up in no logs. I have yenta_socket insmod'd (as well as pcmcia_core and pcmcia) but again, they're not recognized (nothing in lspci, no entry of devices being recognized in dmesg, etc.)

Here's some output.

lspci -vv instances. An old Lucent WaveLAN card (the white variety, 16-bit PCMCIA) is inserted in the first (PCMCIA/Cardbus) slot in this instance:

> 01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
	Subsystem: IBM ThinkPad A/T/X Series
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: f0000000-f3fff000 (prefetchable)
	Memory window 1: d4000000-d7fff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
	Subsystem: IBM ThinkPad A/T/X Series
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=06, subordinate=06, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: d8000000-dbfff000
	I/O window 0: 00003800-000038ff
	I/O window 1: 00003c00-00003cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001


Here are a whole slew of different cards being inserted and removed from the system (last couple lines from dmesg output). The last two are a hybrid CF/802.11 card and a 16M CF card, in that order. /var/log/messages shows similar output.

> [ 2005.444810] pccard: PCMCIA card inserted into slot 0
[ 2015.744346] pccard: card ejected from slot 0
[ 2018.128397] pccard: PCMCIA card inserted into slot 0
[ 2020.258844] pccard: card ejected from slot 0
[ 2022.079500] pccard: CardBus card inserted into slot 0
[ 2024.702697] pccard: card ejected from slot 0
[ 2473.064065] pccard: CardBus card inserted into slot 0
[ 4715.775475] pccard: card ejected from slot 0
[ 4728.090062] pccard: PCMCIA card inserted into slot 0
[ 4737.870944] pccard: card ejected from slot 0
[ 4742.307355] pccard: PCMCIA card inserted into slot 0
[ 5313.680786] pccard: card ejected from slot 0
[ 5381.260529] pccard: PCMCIA card inserted into slot 1
[ 5381.260550] cs: memory probe 0xf0000000-0xf80fffff: excluding 0xf0000000-0xf87fffff
[ 5390.543064] pccard: card ejected from slot 1
[ 5398.686668] pccard: PCMCIA card inserted into slot 1

The first card (socket 0) is the 16M CompactFlash card, and the second is a Lucent WaveLan again.

> /sys/bus/pcmcia# pccardctl status
Socket 0:
  5.0V 16-bit PC Card
Socket 1:
  3.3V 16-bit PC Card

Same cards:

> 
pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available

I should note that this was working fine on my previous install, which was Debian Sid. It was so trivial to get working at the time (and I had it running on sid for a number of years as well) that I don't remember thing one about what I may have done differently.

I looked around on thinkwiki and they didn't have anything which seemed to pertain to this problem. 

Any help would be appreciated.

---

