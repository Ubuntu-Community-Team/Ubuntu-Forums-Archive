---
title: "Finding out what sound card I have?"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by erothoff on 2007-04-19
Hi,
  I guess I need to restart from the beginning to figure out my sound card.  Using aplay -l

I get: (After I manually added the module, sudo /sbin/modprobe snd-intel8x0m)

**** List of PLAYBACK Hardware Devices ****
card 1: Modem [Intel 440MX Modem], device 0: Intel ICH - Modem [Intel 440MX Modem - Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

using lspci -v

I get: 

00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
        Subsystem: Fujitsu Limited. Unknown device 107f
        Flags: bus master, medium devsel, latency 64

00:00.2 Modem: Intel Corporation 82440MX AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Fujitsu Limited. Unknown device 10d1
        Flags: bus master, fast devsel, latency 0, IRQ 9
        I/O ports at 1400 [size=256]
        I/O ports at 1080 [size=128]

00:07.0 Bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1020 [size=16]

00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 15
        I/O ports at 1000 [size=32]

00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
        Flags: medium devsel

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Fujitsu Limited. Unknown device 111c
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 8000 [size=256]
        Memory at fc000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
        Subsystem: Fujitsu Limited. Unknown device 10e6
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 9
        Memory at 30020000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00002000-000020ff
        16-bit legacy interface ports at 0001

00:13.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
        Subsystem: Fujitsu Limited. Unknown device 10e6
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 9
        Memory at 30021000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 28000000-2bfff000 (prefetchable)
        Memory window 1: 2c000000-2ffff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        16-bit legacy interface ports at 0001

00:14.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited. Unknown device 114f
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 9
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1800 [size=256]
        Memory at fc001000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

And the manual says I have a SigmaTel STAC 9723 16-bit stereo audio.
What I have is a Fujitsu Lifebook B Series 2610.

Would the snd-intel8x0m be my sound card or my modem? (Or both) My understanding is that my modem is on a miniPCI card, so I wouldn't think that they are together. But snd-intel8x0 doesn't work.
  All that I googled, said just that the sound works!!!  I get nothing. (Sometimes I can hear a vary faint sound, if I reboot the computer and don't play with the alsamixer. BTW, I have to currently use "-c 1"  for it to pick up the sound driver.

  Any help would be appreciated. I have used linux for a long time, but never, never used sound. (I had it on our server, but not on my PC as a replacement.) I now have just Xubuntu on my Lifebook, as most of what I need is internet, and email. I would like to be able to watch videos, and listen to audio books if possible. (And possibly put Star Craft, Age of Empires II and Rise of Nations on using Wine.) 

Thanks

---

