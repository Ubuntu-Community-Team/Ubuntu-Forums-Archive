---
title: "No Sound on Vaio  E laptop (10.4)"
date: 2010-04-30
forum: Hardware
---

### Post by Eremis on 2010-04-30
Hi everybody!

I just installed ubuntu 10.4 on my 3 week old sony vaio...
Everything works out of the box (even ati graphics) but my sound, I know I have all the codecs installed, and yes my sound is not muted...

Here's the output of "aplay -l" command:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Output from "lspci -v" command:

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e0000000-f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f5e0a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f5e08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4a00000-f5dfffff
	Prefetchable memory behind bridge: 00000000f5f00000-00000000f60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f3600000-f49fffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2200000-f35fffff
	Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0200000-f21fffff
	Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f5e07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f5e06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: medium devsel, IRQ 4
	Memory at f5e05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f5e04000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e017
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4a00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3602000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3601000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3600000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f2220000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Expansion ROM at f2200000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0


```



Can somebody please help me solve this...
(I did a couple of tutorials, but nothing helped...):confused:


Thanks!

---

### Post by lidex on 2010-05-02
You're gonna need alsa 1.0.23:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by Eremis on 2010-05-03
Thank you, it worked perfectly!!!

---

### Post by lidex on 2010-05-05
You're quite welcome. Could you please mark this thread as solved using 'Thread Tools' up top? I have a hunch a lot of Vaio owners will be looking. ;)

---

### Post by davehn on 2010-06-19
:popcorn:I have a SONY VIO VPCEB11FM and I had no sound at all using ubuntu 10.4 I found this link and solved the problem [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695)

also read carefully comment #39 and #48 and I think this might work for a bunch of computers

what this does, it updates the alsa driver to 1.0.23

---

### Post by lidex on 2010-06-19
> **davehn said:**
> :popcorn:I have a SONY VIO VPCEB11FM and I had no sound at all using ubuntu 10.4 I found this link and solved the problem [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695)

also read carefully comment #39 and #48 and I think this might work for a bunch of computers

what this does, it updates the alsa driver to 1.0.23

And this doesn't??
[http://ubuntuforums.org/showpost.php?p=9221151&postcount=2]("http://ubuntuforums.org/showpost.php?p=9221151&postcount=2")

---

