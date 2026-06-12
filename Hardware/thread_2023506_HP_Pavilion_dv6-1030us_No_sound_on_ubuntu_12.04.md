---
title: "HP Pavilion dv6-1030us No sound on ubuntu 12.04"
date: 2012-07-12
forum: Hardware
---

### Post by henrykxxxvll on 2012-07-12
When I upgraded  to ubuntu 12.04 my laptop's speakers had no sound. I've done alsa check but still not working. If someone can help me out to fix this? thanx.

---

### Post by henrykxxxvll on 2012-07-12
I've run this command
sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ lspci -v

this is what I get:

  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 2
     0x10 0x11
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1
Codec: Intel Cantiga HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862802
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 7110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0
	Memory at d5400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 70e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 70c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at da505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at da500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d9500000-da4fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d8500000-d94fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d7500000-d84fffff
	Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6500000-d74fffff
	Prefetchable memory behind bridge: 00000000d3400000-00000000d43fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d5500000-d64fffff
	Prefetchable memory behind bridge: 00000000d4400000-00000000d53fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 70a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 7080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 7060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 7040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at da505800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
	I/O ports at 7108 [size=8]
	I/O ports at 711c [size=4]
	I/O ports at 7100 [size=8]
	I/O ports at 7118 [size=4]
	I/O ports at 7020 [size=32]
	Memory at da505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: medium devsel, IRQ 11
	Memory at da506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 7000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: fast devsel, IRQ 11
	Memory at da504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 137f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d9500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at 5000 [size=256]
	Memory at d1410000 (64-bit, prefetchable) [size=4K]
	Memory at d1400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 7110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0
	Memory at d5400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 70e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 70c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at da505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at da500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d9500000-da4fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d8500000-d94fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d7500000-d84fffff
	Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6500000-d74fffff
	Prefetchable memory behind bridge: 00000000d3400000-00000000d43fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d5500000-d64fffff
	Prefetchable memory behind bridge: 00000000d4400000-00000000d53fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 70a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 7080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 7060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 7040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at da505800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
	I/O ports at 7108 [size=8]
	I/O ports at 711c [size=4]
	I/O ports at 7100 [size=8]
	I/O ports at 7118 [size=4]
	I/O ports at 7020 [size=32]
	Memory at da505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: medium devsel, IRQ 11
	Memory at da506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 7000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: fast devsel, IRQ 11
	Memory at da504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 137f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d9500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3627
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at 5000 [size=256]
	Memory at d1410000 (64-bit, prefetchable) [size=4K]
	Memory at d1400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by jmfal on 2012-07-12
Welcome to Ubuntu 
Run this in a terminal
```
 sudo alsa force-reload   
```

Make sure all speaker volume controls are unmuted and increased to at least 75 in alsammixer

If you are going to play a cd turn up cd control in the alsamixer

---

### Post by henrykxxxvll on 2012-07-13
hey jmfal, thanks for helping me!

I've done it and it didn't worked. This is what I got.
sudo alsa force-reload

sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ sudo alsa force-reload
[sudo] password for sandyhec: 
Unloading ALSA sound driver modules: snd-seq-dummy snd-hrtimer snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hrtimer snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-hrtimer snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by henrykxxxvll on 2012-07-14
Hi, Still not working!!!

---

### Post by jmfal on 2012-07-14
Run this in a terminal

```
 aplay -l   
```

And post results between [CODE][CODE] tag using #

---

### Post by jmfal on 2012-07-14
Try this 
```
 sudo apt-get install --reinstall libasound2    
```

Make sure all speaker and PCM controls are unmuted and set at 75

---

### Post by henrykxxxvll on 2012-07-16
I got this:
#```

sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```#

Hope I did it rigt!

---

### Post by henrykxxxvll on 2012-07-16
I've tried this option but also didn't worked.

---

### Post by jmfal on 2012-07-16
Try this, in a terminal
```
  gksudo gedit  /etc/modprobe.d/alsa-base.conf  
```

Enter your password, a file will open, scroll to end of file and type:

```
  options snd-hda-intel model=dell-m4-3 enable_msi=1     
```

Save/replace in etc folder.
Run these in terminal:
```
    
killall pulseaudio  sudo alsa force-reload  pulseaudio -D      
```
Restart laptop, make sure all speakers are not muted in alsamixer, play some music.
Here is link , all info  here is in first post, if this option doesn't work reopen alsa.base.conf  delete that entry and try another one for "dv6"..
Any problems post back, glad to help.

---

### Post by henrykxxxvll on 2012-07-16
Do I have to back up that file first?

---

### Post by henrykxxxvll on 2012-07-16
this is what I get on the last step:
   ```

         sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ killall pulseaudio  sudo alsa force-reload  pulseaudio -D
D: unknown signal; killall -l lists signals.
   
```
 And thanks for all your time and help!!!! :-)

---

### Post by jmfal on 2012-07-16
You can save it if you want >>copy to documents, just not in etc.

the last command is three commands should run one at a time

killall pulseaudio
sudo alsa force-reload
pulseaudio -D

---

### Post by tyla46 on 2012-07-16
I have the same laptop and same problem.
I followed the directions in this link [http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html](http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html) and sound worked.

---

### Post by henrykxxxvll on 2012-07-17
Ok, jmfal. I got it. It was my mistake. I run them all at once. Let's try, and let you know what happen. Thanks.

---

### Post by henrykxxxvll on 2012-07-17
Ok, this is what I got on the last one:
#
[code]
sandyhec@sandyhec-HP-Pavilion-dv6-Notebook-PC:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
[code]
#

---

### Post by jmfal on 2012-07-17
If that  doesn't work try adding th e options that tyla 46 gave you, the line of options from me may be outdated or might not full use of jacks/etc.

---

### Post by henrykxxxvll on 2012-07-17
Ok let me check it.

---

### Post by henrykxxxvll on 2012-07-17
If I have added this line:
#[code]
options snd-hda-intel model=dell-m4-3 enable_msi=1
[code]
do i have to comment or leave it.

---

### Post by jmfal on 2012-07-17
Don;t ## out 

run those three commands 
restart 
check sound

---

### Post by henrykxxxvll on 2012-07-17
Whit this option speakers are working, but plugging headphones speakers are still working. is there a way to fix it or just deal with it?

Thanks for all your attention and help.

---

### Post by jmfal on 2012-07-17
Yes success.
open that file again comment out the option and add the lines from tyla46

save and close the file

run the three commands
restart
check sound/play music
still problems post back.
If everything is good mark solved using forum tool above.

---

### Post by henrykxxxvll on 2012-07-17
Is this output right when I run this last command:
```

pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.

```

---

### Post by jmfal on 2012-07-17
Yes that's alright ,  the pulse daemon will start up when you restart

---

### Post by henrykxxxvll on 2012-07-17
OK, I have sound on the speakers, even with headphones plugged(they work also) I just wonder if it can be solved. What I did was:
coment this line,
```

options snd-hda-intel model=dell-m4-3 enable_msi=1

```

then add this two lines to **alsa-base.conf** from tyla46 link,
```

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```
then run this three commands,
```

killall pulseaudio
sudo alsa force-reload
pulseaudio -D

```
one at time,
then restart.

This is tyla46 link: 
[http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html](http://thisismyeye.blogspot.com/2012/06/no-sound-on-ubuntu-1204-after-upgrading.html)

Thank you for all your help!!!!

---

### Post by jmfal on 2012-07-17
I'm sure there is a solution for that.
You can go back into that file and uncomment the first option and see what that does.
You can always go back and ## it out if it causes more problems.

Try playing with the controls in alsamixer and see if that helps.

---

### Post by henrykxxxvll on 2012-07-17
OK jmfal I'll give it a try. Thanks a lot.

---

