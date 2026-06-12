---
title: "hp dv7 1020us -- sound issues"
date: 2009-05-10
forum: Hardware
---

### Post by jamied66 on 2009-05-10
All,

I'm trying to get rid of Fedora (long time RHEL user at work), and Ubuntu 9.04 is almost everything I want in a laptop distro.  

except for the sound.

I've foud a TON of info online, and none of it is helping me.

I have:

```

jduncan@jduncan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: d0000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 90e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 90c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at df404c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at df400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: de300000-df3fffff
    Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: dd300000-de2fffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: dc200000-dd2fffff
    Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: db200000-dc1fffff
    Prefetchable memory behind bridge: 00000000d6000000-00000000d70fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: da100000-db1fffff
    Prefetchable memory behind bridge: 00000000d7100000-00000000d80fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d9100000-da0fffff
    Prefetchable memory behind bridge: 00000000d8100000-00000000d90fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 90a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 9080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 9060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 9040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at df404800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
    I/O ports at 9108 [size=8]
    I/O ports at 9114 [size=4]
    I/O ports at 9100 [size=8]
    I/O ports at 9110 [size=4]
    I/O ports at 9020 [size=32]
    Memory at df404000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: medium devsel, IRQ 11
    Memory at df405000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 9000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 8000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
    Subsystem: Intel Corporation Device 1211
    Flags: bus master, fast devsel, latency 0, IRQ 2294
    Memory at de300000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

04:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03)
    Subsystem: Avermedia Technologies Inc Device 1055
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dc200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 2295
    I/O ports at 3000 [size=256]
    Memory at d6010000 (64-bit, prefetchable) [size=4K]
    Memory at d6000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d6020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100000 (32-bit, non-prefetchable) [size=2K]
    Memory at da100d00 (32-bit, non-prefetchable) [size=128]
    Memory at da100c80 (32-bit, non-prefetchable) [size=128]
    Memory at da100c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100b00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: fast devsel, IRQ 11
    Memory at da100a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
    Subsystem: Hewlett-Packard Company Device 30f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

```The trick everyone talked about as the most successful was adding the boot option, "pci=noacpi".  I did this, and my sound still loops (or locks or whatever you want to call it).

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1c6cbb9d-2b01-41f3-bab8-fdea341492f8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1c6cbb9d-2b01-41f3-bab8-fdea341492f8 ro quiet splash pci=noacpi 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```I'm far from a Linux noob, but haven't been involved with Ubuntu since Edgy (well before this laptop).

Any help is appreciated.

thanks.

---

