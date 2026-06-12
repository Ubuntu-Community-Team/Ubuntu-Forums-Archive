---
title: "No sound on AMD 780G based computer"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by madgenius on 2008-03-28
Hi All,

I recently bought an AMD 780G chipset based comp and installed Kubuntu 7.10 on it. Install went fine, and I could even install the Catalyst 8.3 graphics drivers without a hitch. However, there is no sound, although Kmix starts as usual, and recognises the sound card. Amarok plays audio files, flash runs without a hitch - but no sound output for any of these. The soundcard & speakers are fine as I get sound on booting into windows.


Hardware setup is --

AMD Athlon 64 X2 Dual core processor 4000+
Gigabyte GA-MA78GM-S2H chipset
2 x 1024MB 800MHz DDR2 RAM
Western Digital 320GB SATA HDD

Soundcard seems to be recognised.  Please help me sort this out.

Copied below is what seems to be usually asked 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Unknown device 9600
        Subsystem: Advanced Micro Devices [AMD] Unknown device 9600
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: Advanced Micro Devices [AMD] Unknown device 9602 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Unknown device 9602

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] Unknown device 9609 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Unknown device 9600
        Capabilities: [b8] HyperTransport: MSI Mapping

00:11.0 SATA controller: ATI Technologies Inc SB700 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [70] #12 [0010]

00:12.0 USB Controller: ATI Technologies Inc SB700 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:13.0 USB Controller: ATI Technologies Inc SB700 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
        Subsystem: Giga-byte Technology Unknown device 4385
        Flags: 66MHz, medium devsel
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB700 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fa00 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Giga-byte Technology Unknown device a022
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB700 LPC host controller
        Subsystem: ATI Technologies Inc SB700 LPC host controller
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: fdb00000-fdbfffff

00:14.5 USB Controller: ATI Technologies Inc SB700 USB OHCI2 Controller (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fe028000 (32-bit, non-prefetchable) [size=4K]

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 9610 (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device d000
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at ee00 [size=256]
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:05.1 Audio device: ATI Technologies Inc Unknown device 960f
        Subsystem: ATI Technologies Inc Unknown device 960f
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at de00 [size=256]
        Memory at fdaff000 (64-bit, prefetchable) [size=4K]
        Memory at fdae0000 (64-bit, prefetchable) [size=64K]
        [virtual] Expansion ROM at fda00000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [70] Express Endpoint IRQ 1
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
        Capabilities: [d0] Vital Product Data

03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fdcff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fdcf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

```

Thanks for the help

---

### Post by Yellow Pasque on 2008-03-28
See if upgrading ALSA helps: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
There's also a link in there about configuring alsa-base which might be helpful.

Side note: try this to see if they've added the labels for your Unknown Devices yet:
```
sudo update-pciids
```

---

### Post by madgenius on 2008-03-28
I tried what you advised. But this is what I got at the end -

```
aplay -l
aplay: device_list:207: no soundcards found...
```

---

### Post by ruminant1 on 2008-04-03
I have almost the same setup.  I followed the instructions at:

[ubuntuforums.org/archive/index.php/t-673943.html]("http://ubuntuforums.org/archive/index.php/t-673943.html")

and the headphones and spdif are working.  I haven't tested the hdmi yet, but it shows up in aplay:

[COLOR="Blue"]card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]

As you can see, it reports as an ALC882 while it is really an 889a, but it seems to work.

It seems that the link to the driver doesn't work, but it's probably better to get the most recent one off of [Realtek's site]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") anyway.

---

### Post by madgenius on 2008-04-04
Thanks ruminant1. Am at work now - will try what you suggested over the weekend.

---

### Post by JoePub on 2008-04-06
Have the same problem also.  Same gigabyte 780G board.

I have upgraded and installed the latest drivers from Realtek still with no sound via HDMI.

:(

[Edit]

[http://https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/196026]("http://https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/196026")
Should be fixed with the latest linux-ubuntu-modules

---

### Post by prince_niceguy on 2008-05-15
I have the same mobo... and I too have problem of no sound through the hdmi... I will also confirm to the bug.

---

### Post by prince_niceguy on 2008-05-17
I upgraded the bios version to F4 and then changed the settings of sound to ati hdmi and in vlc changed the output device to alsa:ati hdmi and now i have sound through the hdmi. I think the bios update did the trick.

Hope it helps others with the same gigabyte board.

---

