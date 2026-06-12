---
title: "No sound, Compaq Presario 700, VIA sound card"
date: 2008-08-01
forum: Hardware
---

### Post by altonbr on 2008-08-01
Hi everyone,

I'm pretty experienced with Ubuntu/GNOME and have been working with it for almost 2+ years. However, I have Xubuntu on an older laptop (2002-era) which had sound working with Windows XP.

I've done some searching around and there doesn't seem to be a definitive answer for no sound in Xubuntu. Also, it is hard to search for 'via' as most search engines ignore such a word.

I've put everything to 100% in alsamixer via the CLI (except for PCM) and I still hear no sound. I also plugged in external speakers to my headphone jack, and nothing.

Here are my relevant outputs:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
$ cat /proc/asound/pcm
00-00: VIA 82C686A/B rev50 : VIA 82C686A/B rev50 : playback 1 : capture 1
```

```
$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
	Flags: bus master, medium devsel, latency 8
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e8100000-e81fffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Capabilities: <access denied>

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 42)
	Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1840 [size=16]
	Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
	Subsystem: First International Computer, Inc. VA-502 Mainboard
	Flags: bus master, medium devsel, latency 64, IRQ 9
	I/O ports at 1800 [size=32]
	Capabilities: <access denied>

00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
	Subsystem: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
	Flags: medium devsel, IRQ 10
	Capabilities: <access denied>

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
	Subsystem: Compaq Computer Corporation SoundMax Digital Integrated Audio
	Flags: medium devsel, IRQ 5
	I/O ports at 1000 [size=256]
	I/O ports at 1854 [size=4]
	I/O ports at 1850 [size=4]
	Capabilities: <access denied>

00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
	Subsystem: Compaq Computer Corporation Unknown device 8d88
	Flags: medium devsel, IRQ 4
	Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 1858 [size=8]
	Capabilities: <access denied>

00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Compaq Computer Corporation Unknown device b103
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at ffbfe000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002000-000020ff
	16-bit legacy interface ports at 0001

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1400 [size=256]
	Memory at e8010000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Compaq Computer Corporation Unknown device 0086
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at e8100000 (32-bit, non-prefetchable) [size=512K]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at e8180000 [disabled] [size=64K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
	Subsystem: Linksys Unknown device 0019
	Flags: medium devsel, IRQ 11
	I/O ports at 1c00 [disabled] [size=256]
	Memory at 14000000 (32-bit, non-prefetchable) [disabled] [size=512]
	Capabilities: <access denied>

```

Anything else you want pasted, just ask.

I appreciate the help! I know these types of threads are common.

---

### Post by altonbr on 2008-08-03
Maybe its not supported?
[https://bugs.launchpad.net/ubuntu/+bug/180009](https://bugs.launchpad.net/ubuntu/+bug/180009)

One person said he could get it working when he "disabled the internal sound card":
[https://bugs.launchpad.net/ubuntu/+bug/225436](https://bugs.launchpad.net/ubuntu/+bug/225436)

Not sure what I can do...

---

