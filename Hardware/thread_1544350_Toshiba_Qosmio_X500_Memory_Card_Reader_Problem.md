---
title: "Toshiba Qosmio X500 Memory Card Reader Problem"
date: 2010-08-02
forum: Hardware
---

### Post by Marcelo Ruiz on 2010-08-02
Hi,

I have a problem in Lucid x64 with my memory card reader. When I insert a memory card I can read the following in the kern.log:

```

Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299339] mmc0: Unexpected interrupt 0x02000000.
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299346] sdhci: ============== REGISTER DUMP ==============
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299357] sdhci: Sys addr: 0x00000000 | Version:  0x0000c401
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299368] sdhci: Blk size: 0x00007008 | Blk cnt:  0x00000001
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299378] sdhci: Argument: 0x00000000 | Trn mode: 0x00000013
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299389] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000011
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299399] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299410] sdhci: Wake-up:  0x00000000 | Clock:    0x00004007
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299420] sdhci: Timeout:  0x0000000a | Int stat: 0x02008000
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299431] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299441] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299452] sdhci: Caps:     0x01fe32b2 | Max curr: 0x00000064
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299462] sdhci: ADMA Err: 0x00000007 | ADMA Ptr: 0x22dee808
Aug  2 11:10:38 marcelo-laptop kernel: [ 6421.299465] sdhci: ===========================================
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292885] mmc0: Timeout waiting for hardware interrupt.
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292888] sdhci: ============== REGISTER DUMP ==============
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292896] sdhci: Sys addr: 0x00000000 | Version:  0x0000c401
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292904] sdhci: Blk size: 0x00007008 | Blk cnt:  0x00000001
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292913] sdhci: Argument: 0x00000000 | Trn mode: 0x00000013
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292920] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000011
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292928] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292936] sdhci: Wake-up:  0x00000000 | Clock:    0x00004007
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292944] sdhci: Timeout:  0x0000000a | Int stat: 0x00000000
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292952] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292960] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292968] sdhci: Caps:     0x01fe32b2 | Max curr: 0x00000064
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292977] sdhci: ADMA Err: 0x00000007 | ADMA Ptr: 0x22dee808
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.292978] sdhci: ===========================================
Aug  2 11:10:48 marcelo-laptop kernel: [ 6431.293009] mmc0: error -110 whilst initialising SD card

```

lspci -v is as follows:

```

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: fast devsel
	Capabilities: [40] #00 [0000]

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-cdefffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
	Capabilities: [40] Subsystem: Intel Corporation Device 0000
	Capabilities: [60] Message Signalled Interrupts: Mask+ 64bit- Queue=0/1 Enable+
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [150] Access Controls <?>
	Capabilities: [160] Vendor Specific Information <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information <?>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information <?>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information <?>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
	Subsystem: Device 0079:0050
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0906000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f0900000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0000000-f03fffff
	Prefetchable memory behind bridge: 00000000f0a00000-00000000f0bfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 00000000c0100000-00000000c02fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0600000-f06fffff
	Prefetchable memory behind bridge: 00000000c0300000-00000000c04fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000c0500000-00000000c06fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0907000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
	I/O ports at 1830 [size=8]
	I/O ports at 1824 [size=4]
	I/O ports at 1828 [size=8]
	I/O ports at 1820 [size=4]
	I/O ports at 1800 [size=32]
	Memory at f0908000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: medium devsel, IRQ 10
	Memory at f0909000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0cb1 (rev a2)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at cdefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

07:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0500000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [200] Advanced Error Reporting <?>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

07:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0501000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [200] Advanced Error Reporting <?>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

07:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0503000 (32-bit, non-prefetchable) [size=4K]
	Memory at f0502000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [a0] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [200] Advanced Error Reporting <?>

0a:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 4000 [size=256]
	Memory at f0600000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

0b:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 5000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-a9-0a-c8-1a-15-f2-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0


```

Do you have any ideas on how to correct this problem?
Thanks!

---

### Post by ineya on 2010-10-26
Did you make any progress? I have the same problem.

---

### Post by vdubhack on 2010-10-29
I have a x505-886 and had the same card reader issue and right now I am trying this current work around. This was not for the O2 micro in the post I found it in but so far things seem ok nothing related to it seems effected.

To make sd card reader work make a conf file in /etc/modprobe.d/  with this 
# Disable ADMA to workaround a sequence of errors which looks like:
#   mmc0: error -110 whilst initialising SD card
#   mmc0: ADMA error
#   mmc0: Got data interrupt 0x02000000 even though no data operation was in progress. 
# when an SD card is inserted to the card reader on a Toshiba X505-886
# See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043)

options sdhci debug_quirks=0x40

Then rmmod sdhci_pci and rmmod sdhci
and then modprobe sdhci and modprobe sdhci_pci

For me though this does not stay through rebooting :( but if you do the above commands again it works until reboot. 

YMMV 
here is what lspci says my card is  SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) (prog-if 01)
Hope this helps some, and if you figure out something better post here.

Here is what mine says before putting it in then with this work around 
[ 2008.894338] mmc0: ADMA error
[ 2008.894373] mmc0: error -5 whilst initialising SD card

After work around has been applied.
[ 2243.828115] sdhci-pci 0000:07:00.1: PCI INT C disabled
[ 2261.816949] sdhci: Secure Digital Host Controller Interface driver
[ 2261.816953] sdhci: Copyright(c) Pierre Ossman
[ 2268.772913] sdhci-pci 0000:07:00.1: SDHCI controller found [1217:8120] (rev 1)
[ 2268.772940] sdhci-pci 0000:07:00.1: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[ 2268.773000] sdhci-pci 0000:07:00.1: setting latency timer to 64
[ 2268.773050] Registered led device: mmc0::
[ 2268.773094] mmc0: SDHCI controller on PCI [0000:07:00.1] using DMA
[ 2269.302634] mmc0: new high speed SDHC card at address 1234
[ 2269.363642] mmcblk0: mmc0:1234 SA08G 7.42 GiB 
[ 2269.363718]  mmcblk0: p1 p2
[ 2272.138576] EXT3-fs: barriers not enabled
[ 2272.161872] kjournald starting.  Commit interval 5 seconds
[ 2272.181383] EXT3-fs (mmcblk0p2): using internal journal
[ 2272.181392] EXT3-fs (mmcblk0p2): mounted filesystem with ordered data mode

---

### Post by Marcelo Ruiz on 2010-10-30
Hi,

Thanks for the info. A small correction from the thread you mentioned: it's sdhci-pci instead of sdhci_pci.
I tried what you mentioned here but nothing happens when I insert the memory card.

After enterning the rmmod commands, I get:

```
sdhci-pci 0000:07:00.1: PCI INT C disabled
```

After entering the modprobe commands:

```

sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pci 0000:07:00.1: SDHCI controller found [1217:8120] (rev 1)
sdhci-pci 0000:07:00.1: PCI INT C -> GSI 17 (level, low) -> IRQ 17
sdhci-pci 0000:07:00.1: setting latency timer to 64
Registered led device: mmc0::
mmc0: SDHCI controller on PCI [0000:07:00.1] using DMA

```

but when I insert the memory card, nothing happens...
Are you able to read the memory card? What version of Ubuntu are you using? Can you post the results of "uname -a"?
Mine is: 

```
Linux marcelo-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
```

I'm using Ubuntu 10.04LTS.

Thanks!

---

### Post by vdubhack on 2010-10-30
I am on 10.10 running the proposed Kernel .35-23, I think. Though were I got this work around was from someone running 9.10. Not sure why yours is - and not _, all I have read always says its _. Did you create the file I said that had to be created, and install it were I said? Did you remove both the sdhci and the sdhci-pci? Both need to be removed, it did not work for me when I only did the pci one. If this doesnt work for you I am not sure why not and wouldnt know what else to try. This fix was not even for the Toshibas just happens to work.   I finally got mine to stay with reboots and everything has been good since for me at least but as always with linux YMMV and I do not think Kernel version is an issue. :)

---

### Post by Marcelo Ruiz on 2010-10-30
Hi Vdubhack,

Yes, I followed your instructions to the letter. After no luck with it, I read the thread of the link you posted and there I found out that it was - instead of _ but still no luck.
I am running 10.04... I guess I will wait until it is solved in the Kernel...
Thanks again!

---

### Post by vdubhack on 2010-10-30
Sorry it did not work out for you. Not sure why its not :( If I run across any other work arounds I will post back. Though as you can tell me being on Kernel .35-23, its one of those things thats been around for awhile. Toshiba issues seem from my recent research to be same ones that have been around as long as 07. I found posts relating to the same SD card and errors I was getting as far back as early 09 and on Ubuntu 9.04  Maybe try checking the permissions of the file, maybe for some reason the file you made does not have the correct ones set. Only other thing at this point I can think of is I named my file SD-CardWorkAround.conf, does your have the .conf?   Lastly you could always try testing with the .35 Kernel and do the same fix and see if that solves it for you, could be a combo of things that changed in .35 to make it work for me on mine.   Good luck

---

### Post by ineya on 2010-12-14
I have Toshiba x505-11z, and the advice with debug_quirks=0x40 worked for me. The SD card was in the pc at the time I did rmmod and modprobe.

---

### Post by olawlor on 2010-12-31
According to the bug report, to make the fix persist across reboots, you need to "sudo update-initramfs -u".  This works on my Toshiba X505-Q893 under 64-bit 10.04.  Curiously in 32-bit Ubuntu 8.04, the SD card reader worked fine without any tweaking.

Here's the whole setup, if you just want to copy-and-paste:
```

sudo su

cat > /etc/modprobe.d/toshiba_sd_reader.conf << EOF
# Disable ADMA to workaround a sequence of errors which looks like:
#    mmc0: Unexpected interrupt 0x02000000.
#     mmc0: error -110 whilst initialising SD card
# when an SD card is inserted to the card reader on a Toshiba X505
# See https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043
# or http://ubuntuforums.org/showthread.php?t=1544350

options sdhci debug_quirks=0x40
EOF

rmmod sdhci_pci sdhci
modprobe sdhci
modprobe sdhci_pci
update-initramfs -u

exit

```

---

### Post by HalfEmptyHero on 2011-01-06
> **olawlor said:**
> According to the bug report, to make the fix persist across reboots, you need to "sudo update-initramfs -u".  This works on my Toshiba X505-Q893 under 64-bit 10.04.  Curiously in 32-bit Ubuntu 8.04, the SD card reader worked fine without any tweaking.

Here's the whole setup, if you just want to copy-and-paste:
```

sudo su

cat > /etc/modprobe.d/toshiba_sd_reader.conf << EOF
# Disable ADMA to workaround a sequence of errors which looks like:
#    mmc0: Unexpected interrupt 0x02000000.
#     mmc0: error -110 whilst initialising SD card
# when an SD card is inserted to the card reader on a Toshiba X505
# See https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043
# or http://ubuntuforums.org/showthread.php?t=1544350

options sdhci debug_quirks=0x40
EOF

rmmod sdhci_pci sdhci
modprobe sdhci
modprobe sdhci_pci
update-initramfs -u

exit

```

I tried this exactly on my x505 q880 on 10.10 but my sd card is still not read.

Edit: Nevermind. I tried a different sd card and it worked. I guess the one I was trying went bad.

---

### Post by AmanicA on 2011-02-26
Thanks a lot olawlor your script works beautifully!

---

### Post by HalfEmptyHero on 2011-04-22
Just to let you know, this doesn't work on a fresh install of natty beta 2.

Edit: It also doesn't work after upgrading from maverick.

---

### Post by sabbyATL on 2012-06-10
> **olawlor said:**
> According to the bug report, to make the fix persist across reboots, you need to "sudo update-initramfs -u".  This works on my Toshiba X505-Q893 under 64-bit 10.04.  Curiously in 32-bit Ubuntu 8.04, the SD card reader worked fine without any tweaking.

Here's the whole setup, if you just want to copy-and-paste:
```

sudo su

cat > /etc/modprobe.d/toshiba_sd_reader.conf << EOF
# Disable ADMA to workaround a sequence of errors which looks like:
#    mmc0: Unexpected interrupt 0x02000000.
#     mmc0: error -110 whilst initialising SD card
# when an SD card is inserted to the card reader on a Toshiba X505
# See https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043
# or http://ubuntuforums.org/showthread.php?t=1544350

options sdhci debug_quirks=0x40
EOF

rmmod sdhci_pci sdhci
modprobe sdhci
modprobe sdhci_pci
update-initramfs -u

exit

```


I know this is an oldish thread but I wanted to say this solution worked for me.

I am running Mint 12 on a Qosmio x500 (18.4 inch screen - wooo!)

The SD card is a 32G SDHC from my Canon T3.


Figured someone might be in a similar situation as I.

Thanks a lot for this solution.  It's much appreciated.

---

