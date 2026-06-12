---
title: "No sound from sound card"
date: 2008-08-13
forum: Hardware
---

### Post by Monkey_Kicker on 2008-08-13
Hello,

I am new to using Ubuntu 8.04.  I am attempting to set up Ubuntu on an old p3 system with on-board sound.  The only problem that I am having is that I can not hear any sound.  As far as I can tell the sound card is being detected correctly, but I am unable to hear anything.  

I checked to make sure mute is off, and the speakers are plugged into the correct jack.  The sound card also works in windows so I know it does work.

The motherboard is a Tyan Trinity 400 (S1854A).  According to Tyan's website the on-board sound is Creative ES1373.  I am not sure if this is the reason the sound is not working.

I would appreciate it if anyone could give me some advice on what to do next.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
	Flags: bus master, medium devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 2.0
	Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [80] Power Management version 2

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
	Subsystem: VIA Technologies, Inc. VT82C596/A/B PCI to ISA Bridge
	Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at d000 [size=16]
	Capabilities: [c0] Power Management version 2

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11) (prog-if 00 [UHCI])
	Subsystem: First International Computer, Inc. VA-502 Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at d400 [size=32]
	Capabilities: [80] Power Management version 2

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
	Flags: medium devsel

00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
	Subsystem: Micron Tazer
	Flags: bus master, slow devsel, latency 32, IRQ 5
	I/O ports at d800 [size=64]
	Capabilities: [dc] Power Management version 1

00:10.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15) (prog-if 00 [VGA controller])
	Subsystem: VISIONTEK Unknown device 000e
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 10
	Memory at d6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d4000000 (32-bit, prefetchable) [size=32M]
	[virtual] Expansion ROM at 20020000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 1

00:12.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
	Subsystem: 3Com Corporation 3C905CX-TX/TX-M Fast Etherlink for PC Management NIC
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at dc00 [size=128]
	Memory at d8000000 (32-bit, non-prefetchable) [size=128]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2

00:13.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 00 [Generic])
	Subsystem: Aztech System Ltd Unknown device 0001
	Flags: medium devsel, IRQ 11
	I/O ports at e000 [size=64]
	Capabilities: [40] Power Management version 2

```

---

### Post by Monkey_Kicker on 2008-08-14
bump

---

### Post by Monkey_Kicker on 2008-08-15
It seems that sound files will start playing, but I hear no sound from the speakers.  The speakers do work and are plugged into the correct port.
I have followed the steps located in the comprehensive sound guide and have not be able to resolve my problem.

Any help would be much appreciated.

---

### Post by markbuntu on 2008-08-15
What is the volume control setting?
(the little speaker in the top panel)
Is it for the wrong sound card?
You can right click on it to find out.

---

### Post by Monkey_Kicker on 2008-08-19
As far as I can tell the correct card is selected and the volume is set to about 90%.

---

### Post by Yellow Pasque on 2008-08-19
Some random thoughts from my drunken head:

- Creative bought out Ensoniq and re-branded the chips. Nevertheless, the ens1371 driver is what you want
- The sound device is on the same IRQ with the Ethernet device. (IRQ5)
- Try OSS4 if all else fails

---

### Post by professir on 2008-08-19
I have a similar issue but my sound only works when plugged in, if I unplug the connector from my laptop the sound doesn't play through the laptop speakers.

---

### Post by cariboo on 2008-08-19
If it your sound card seems to be playing a sound, in a Applications-->Accessories-->Terminl type:

```
alsamixer
```

Use the arrow keys and the tab keys to navigate. Make sure that pcm  and volume are turned up.

Jim

---

### Post by Monkey_Kicker on 2008-08-23
I have set the volume using alsamixer to no avail.

I did happen to notice that the sound card was on the same IRQ as the lan card.  However, I have no idea how to change this in Ubuntu.  I have only had experience changing it in windows. I am not sure if this is an issue.  I have seen devices share an interrupt before with no problems, and I believe it was working in Windows Me on the same interrupt as the lan.

I suppose I will try OSS4 if I can not come up with anything.

Thanks.

---

