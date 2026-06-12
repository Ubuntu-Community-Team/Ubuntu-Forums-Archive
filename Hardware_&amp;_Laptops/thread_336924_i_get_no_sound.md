---
title: "i get no sound"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by atlfalcons866 on 2007-01-12
hi i have no sound but my usb speakers are on. i am not sure what my soundcard is though

Edit
solved

---

### Post by mistafeesh on 2007-01-12
Hi,

For people to help, you'll probably need to supply a bit more info than that!! Such as what laptop, what USB speakers, etc.

Sorry to piggyback onto this, but I'm having the same problem, and I thought it'd be silly to start a new thread... I've got a Dell Latitude CP1 D300XT, and the [specs]("http://support.dell.com/support/edocs/systems/pmojav/specs.htm") from the Dell website say this has a Crystal 4237B soundblaster pro compatible audio controller. Any ideas?


Dan

edit - just found [this article]('http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide') which gives lots of suggestins for fixing the sound.

running the terminal command "aplay -l" lists no soundcards, and lspci -v doesn't seem to list a sound card.... as the sound should be an onboard thing, I guess this may be a bios problem, but I can't get into the bios!!!

---

### Post by atlfalcons866 on 2007-01-12
this is what i get i really dont know what i am doing.

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by atlfalcons866 on 2007-01-12
and if this helps too

jack@jack-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Subsystem: VIA Technologies, Inc. P4M800CE Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: f4000000-f7ffffff
        Capabilities: <access denied>

00:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Netgear Unknown device 6b00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fdfd0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at f800 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at f400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at f000 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at ec00 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd. Unknown device b014
        Flags: medium devsel, IRQ 193
        I/O ports at e800 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 185
        I/O ports at e400 [size=256]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=64K

---

### Post by haiku99 on 2007-01-12
see [http://ubuntuforums.org/showthread.php?t=312040](http://ubuntuforums.org/showthread.php?t=312040)       and
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by atlfalcons866 on 2007-01-12
i have sound but they dont come out of my usb speakers.

---

