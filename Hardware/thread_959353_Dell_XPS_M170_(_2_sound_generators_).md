---
title: "Dell XPS M170 ( 2 sound generators )"
date: 2008-10-26
forum: Hardware
---

### Post by Flatsvisconti on 2008-10-26
I have a dell XPS M170 with Hardy and all updates.  It seems whenever sound plays there are two sounds.  I know this is kind of wierd, I don't know how to explain it.  Whenever any sound plays, I can turn down the volume or mute it and I can still here the sound but a little more bassy.  It seems like when I turn the sound down, I turn one of them down but the other one I can't change.  I ran aplay -l at got this reply

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am using the alsa mixer 

I run lspci and get this reply

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dd000000-dfefffff
        Prefetchable memory behind bridge: c0000000-cfffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
        Memory behind bridge: dcf00000-dcffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ed00 [size=256]
        I/O ports at ec40 [size=64]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Dell Unknown device 01aa
        Flags: medium devsel, IRQ 10
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7800 GTX] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device 019c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at df00 [size=128]
        [virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at dcff0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: <access denied>

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dcf00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at dcfee800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
        Subsystem: Dell Unknown device 01aa
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dcfee700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Dell B130 laptop integrated WLAN
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dcfef000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

I have been in the ubuntu irc rooms and searched the net but can't seem to troubleshoot this problem.  Any help would be greatly appreciated.

Thanks

Frank

---

### Post by mrb88 on 2008-11-03
I have the M170 also. Here's the deal: "Master" and "Master Mono" are the front two speakers and the subwoofer. You should balance them out, make it sound good, and then change volume control to use PCM instead of Master/Master Mono. You can change what the volume buttons control in the Sound settings in Gnome.

---

