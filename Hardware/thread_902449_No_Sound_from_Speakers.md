---
title: "No Sound from Speakers"
date: 2008-08-27
forum: Hardware
---

### Post by ivodalves on 2008-08-27
Hi,

I'm running Ubuntu 8.04 in a Toshiba Tecra A8. Everything is ok except the sound.
I can hear sound from headphones but not from the speakers.
Does anyone know how to solve this?

I've no "muted" output
and the ubuntu detects the soundcard

> ivo@ivo-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> ivo@ivo-laptop:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device 0005
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ffd80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at cff8 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at ffd40000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device 0005
	Flags: fast devsel
	Memory at a8000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>
[B][I]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at a8080000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>[/I][/B]

[B]00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ffc00000-ffcfffff
	Capabilities: <access denied>[/B]

[B]00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ffa00000-ffafffff
	Capabilities: <access denied>[/B]

[B]00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at afe0 [size=32][/B]

[B]00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at af80 [size=32][/B]

[B]00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at af60 [size=32][/B][/B]

[B]00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at af40 [size=32][/B]

[B]00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffd3fc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at af10 [size=16]
	Capabilities: <access denied>[/B]

01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 508
	Memory at ffce0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at bfe0 [size=32]
	Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1041
	Flags: bus master, fast devsel, latency 0, IRQ 509
	Memory at ffaff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at a8088000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: ac000000-affff000 (prefetchable)
	Memory window 1: b0000000-b3fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at a8089000 (32-bit, non-prefetchable) [size=2K]
	Memory at a8084000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at a8089800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



Thanks

---

### Post by ivodalves on 2008-09-17
Hi,
[B]
problem solved[/B] for **Toshiba Tecra A8**!

edit alsa-base file

**sudo gedit /etc/modprobe.d/alsa-base**

add the following line to the end of the file:

**options snd-hda-intel enable=1 index=0 model=basic**

save and reboot!

and that's it! Works perfectly!

Best regards,

Ivo

---

