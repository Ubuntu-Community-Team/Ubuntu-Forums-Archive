---
title: "Sony Vaio Tap 11 vs. Ubuntu vs. Driver Issues"
date: 2014-03-27
forum: Hardware
---

### Post by zolkin on 2014-03-27
[FONT=arial]I just installed Ubuntu 13.10 on my new Sony Vaio Tap 11:
[/FONT][COLOR=#7C7E8B][FONT=arial]4th gen Intel® Core™ i7-4610Y (1.70GHz / 2.90GHz)
[/FONT][/COLOR][COLOR=#7C7E8B][FONT=arial]11.6" Full HD IPS touch display (1920 x 1080)
[/FONT][/COLOR][COLOR=#7C7E8B][FONT=arial]8GB RAM
256GB SSD
[/FONT][/COLOR][COLOR=#7C7E8B][FONT=arial]Intel® HD Graphics 4200
[/FONT][/COLOR][COLOR=#7C7E8B][FONT=arial]Micro HDMI® out, USB 3.0, NFC
[/FONT][/COLOR][COLOR=#7C7E8B][FONT=arial]Wireless keyboard cover, Active Pen
[/FONT][/COLOR]I tried other versions of (K)Ubuntu 12.04, 12.10, 13.04. Among all of them this one looks more stable than others.
Obviously (since this is Sony Vaio) I have few (ALOT) issues I would like to fix.

Here is the list of things I would like to fix in priority order:
1) Most important issue, is that after one week of working relatively Ok, ma laptop somehow lost driver for battery. So now the laptop is turning on only if its plugged to the charger. An attempt to unplug leads to immediate shutdown. Also the battery sign on dashboard disappeared.
2) At the same time I lost the driver for the wireless Keyboard coming with laptop. The keyboard is charged and have all indicators running, while laptop do not react on any key pres. Also before I lost the driver, Keyboard was working as well as trackpad on it (but mouse-like buttons associated with this track-pad, never worked).
3) The quality of sound sometimes is very bad - it became noise and chatter (for no reason, like you listening music and suddenly quality drops down). I'm sure I have 3 speakers (2 side ones and one on top), while only side ones working. Alsa mixer looking very "poor" and do not provide many options (see attached picture)
4) I have a sensor pen coming with Laptop. It is also not well supported on a hardware level. Let say I can use buttons on it but it is not working properly all the time. Is it fixble?
5) It does not look like I fully can support Wacom Tablet, probably it requires extra driver or something.
6*) If it is possible I would like to know how I can activate gravitometr/accelerometr to rotate screen image along with device rotations.
7**) If it is possible I would like to know can I use milti-touch (or maybe its better to wait till (K)Ubuntu 14.04 - any ideas)

Here is some info about what I have now:
```

bender@BendingUnit22:~$ kde4-config --version
Qt: 4.8.4
KDE Development Platform: 4.11.5
kde4-config: 1.0

```

```

bender@BendingUnit22:~$ ls /etc/apt/sources.list.d
ehoover-compholio-saucy.list  google-talkplugin.list  google-talkplugin.list.save

```

```

bender@BendingUnit22:~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 0a1e (rev 0b)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

```

```

bender@BendingUnit22:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:02.0 VGA compatible controller: Intel Corporation Device 0a1e (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, fast devsel, latency 0, IRQ 63
    Memory at b2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at b2510000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) (prog-if 30 [XHCI])
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, medium devsel, latency 0, IRQ 59
    Memory at b2500000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, fast devsel, latency 0, IRQ 61
    Memory at b2518000 (64-bit, non-prefetchable) [size=32]
    Capabilities: <access denied>
    Kernel driver in use: mei_me


00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, fast devsel, latency 0, IRQ 65
    Memory at b2514000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: b2400000-b24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.5 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 6 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=08, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b1000000-b1ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000b0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b251c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich


00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Sony Corporation Device 90bb
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 60
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at b251b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
    Subsystem: Sony Corporation Device 90bb
    Flags: medium devsel
    Memory at b2519000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]


02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260
    Flags: bus master, fast devsel, latency 0, IRQ 62
    Memory at b2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

```

---

