---
title: "Not able to mount SD card"
date: 2011-02-10
forum: Hardware
---

### Post by modaslam on 2011-02-10
Linux-laptop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5050 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d6406100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d6405c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d5400000-d63fffff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4400000-d53fffff
    Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d3400000-d43fffff
    Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d6405800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 32
    I/O ports at 5048 [size=8]
    I/O ports at 505c [size=4]
    I/O ports at 5040 [size=8]
    I/O ports at 5058 [size=4]
    I/O ports at 5020 [size=32]
    Memory at d6405000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: medium devsel, IRQ 10
    Memory at d6406000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d6404000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d3400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0
[CODE]

```[41520.303764] usblp0: removed
[41607.710966] usb 1-1.1: USB disconnect, address 3
[47079.179312] usb 1-1.1: new high speed USB device using ehci_hcd and address 4
[47079.272248] usb 1-1.1: configuration #1 chosen from 1 choice
[47079.273456] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7811
[47080.969117] usb 1-1.1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[47259.003521] usb 1-1.1: USB disconnect, address 4
[47259.003943] usblp0: removed
[49361.057331] FAT: bogus logical sector size 65535
[49361.057348] VFS: Can't find a valid FAT filesystem on dev sda3.
[/CODE]```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       18856   149920768    7  HPFS/NTFS
/dev/sda3           18856       37377   148766721    f  W95 Ext'd (LBA)
/dev/sda4           37377       38914    12344320   17  Hidden HPFS/NTFS
/dev/sda5           18856       29703    87122944    7  HPFS/NTFS
/dev/sda6           29703       32192    19998720   83  Linux
/dev/sda7           32193       32690     3998720   82  Linux swap / Solaris
/dev/sda8           32690       34807    16999424   83  Linux
/dev/sda9           34807       36052     9999360   83  Linux
/dev/sda10          36052       37377    10642432   83  Linux


```

---

### Post by dabl on 2011-02-10
That is probably a USB device, meaning it will not appear in the PCI bus list -- only the USB controller shows up there.

Try inserting your SD card, and then (after a few seconds) in the terminal do

```
lsusb
```

and see if it shows up there.

---

### Post by modaslam on 2011-02-11
```

Bus 002 Device 005: ID 0930:0214 Toshiba Corp. 
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

