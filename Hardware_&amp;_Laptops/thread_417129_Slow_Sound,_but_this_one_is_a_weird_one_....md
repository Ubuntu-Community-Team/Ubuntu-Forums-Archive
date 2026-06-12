---
title: "Slow Sound, but this one is a weird one ..."
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by samae on 2007-04-21
Here is my problem :
Ever since I had Edgy everything was all right. And then I updated to Feisty.
It fixed a lot of little bugs here and there but it disturbed my audio system : now my laptop give me the impression of running in slow motion in fact it plays sounds very slowly ...

I've tried many tricks to know were it came from by I'm desperate now, and I guess it's not comming from alsa :s

Anyway this was my problem, and here follows my config and some tests :

```

tail -2 /proc/asound/oss/sndstat
Mixers:
0: Realtek ALC650F
```

```

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-16.50dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-1.50dB] [on]
  Front Right: Playback 22 [71%] [-1.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Independent'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 19 [61%] [-6.00dB] [on] Capture [off]
  Front Right: Playback 19 [61%] [-6.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-4.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 2 [67%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 10 [67%] [15.00dB] [on]
  Front Right: Capture 10 [67%] [15.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```

```

lspci -nv
00:00.0 0600: 1039:0756 (rev 02)
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 32
        Capabilities: <access denied>

00:01.0 0604: 1039:0004 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fa200000-fe2fffff
        Prefetchable memory behind bridge: 00000000bde00000-00000000ddefffff
        Capabilities: <access denied>

00:02.0 0601: 1039:0964 (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 0101: 1039:5513 (rev 01) (prog-if 80 [Master])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 128
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.6 0703: 1039:7013 (rev a0) (prog-if 00 [Generic])
        Subsystem: 1043:1816
        Flags: medium devsel, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

00:02.7 0401: 1039:7012 (rev a0)
        Subsystem: 1043:1103
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:03.0 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]

00:03.1 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]

00:03.2 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]

00:03.3 0c03: 1039:7002 (prog-if 20 [EHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 0280: 14e4:4318 (rev 02)
        Subsystem: 1043:120f
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at febfa000 (32-bit, non-prefetchable) [size=8K]

00:0a.0 0607: 1180:0476 (rev b3)
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at 58000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:0a.1 0c00: 1180:0552 (rev 08) (prog-if 10 [OHCI])
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at febf9800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:0a.2 0805: 1180:0822 (rev 17)
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at febf9400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0a.3 0880: 1180:0592 (rev 08)
        Subsystem: 1043:1977
        Flags: medium devsel, IRQ 5
        Memory at febf9000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0b.0 0200: 10ec:8139 (rev 10)
        Subsystem: 1043:1045
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d800 [size=256]
        Memory at febf8c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 0600: 1022:1100
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 0600: 1022:1101
        Flags: fast devsel

00:18.2 0600: 1022:1102
        Flags: fast devsel

00:18.3 0600: 1022:1103
        Flags: fast devsel

01:00.0 0300: 10de:0167 (rev a1) (prog-if 00 [VGA])
        Subsystem: 1043:188a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fe2e0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 0280: 14e4:4318 (rev 02)
        Subsystem: 1737:0049
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at 54000000 (32-bit, non-prefetchable) [size=8K]
```


```

asoundconf list
Names of available sound cards:
SI7012
```

I haven't modified the default options in /etc/asound.conf

Only APIC errors in dmesg (so it should have nothing to do with it) :
APIC error on CPU0: 40(40)


```
cat /proc/interrupts
           CPU0       
  0:    1220416   IO-APIC-edge      timer
  1:         12   IO-APIC-edge      i8042
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc
  9:      41894   IO-APIC-fasteoi   acpi
 12:        133   IO-APIC-edge      i8042
 14:      47833   IO-APIC-edge      ide0
 15:      43399   IO-APIC-edge      ide1
 16:     326391   IO-APIC-fasteoi   nvidia
 17:     326709   IO-APIC-fasteoi   yenta, bcm43xx
 18:      68323   IO-APIC-fasteoi   ohci1394, SiS SI7012
 19:          0   IO-APIC-fasteoi   sdhci:slot0
 20:       9169   IO-APIC-fasteoi   ohci_hcd:usb1
 21:     112730   IO-APIC-fasteoi   ohci_hcd:usb2
 22:          0   IO-APIC-fasteoi   ohci_hcd:usb3
 23:      12908   IO-APIC-fasteoi   ehci_hcd:usb4
NMI:          0 
LOC:    1220276 
ERR:         48
```

And I'm running Xubuntu 64bit 7.04

What else ... the whole system plays sounds slow (funny indeed but boring) ...

---

