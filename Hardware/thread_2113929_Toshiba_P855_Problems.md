---
title: "Toshiba P855 Problems"
date: 2013-02-08
forum: Hardware
---

### Post by xastey on 2013-02-08
I just purchased a Toshiba P855 and ran a LiveUSB 12.10 install but ran into a few problems with my hardware.
1) The fn keys to control the screen brightness isn't working
2) The keyboard backlit doesn't toggle ,  I pressed fn+Z and get a display in the top right corner similar to the one for volume ( the volume function keys work just fine)
3) [Solved] Wifi is not being picked up.

Edit:
So solved my wifi issues thanks to another thread [http://ubuntuforums.org/showthread.php?p=12444800#post12444800](http://ubuntuforums.org/showthread.php?p=12444800#post12444800), had to changed the driver to remove but worked.

Here are some outputs to help:
```

ubuntu@ubuntu:~$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

``````

ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device fb00
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fb00
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at bfc00000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at c0c00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c0c1a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c0c18000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at c0c10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0b00000-c0bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: c0a00000-c0afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c0000000-c09fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000e09fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c0c17000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 40b0 [size=8]
    I/O ports at 40a0 [size=4]
    I/O ports at 4090 [size=8]
    I/O ports at 4080 [size=4]
    I/O ports at 4060 [size=32]
    Memory at c0c16000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: medium devsel, IRQ 11
    Memory at c0c15000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 3000 [size=256]
    Memory at c0b04000 (64-bit, prefetchable) [size=4K]
    Memory at c0b00000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN
    Flags: fast devsel, IRQ 17
    Memory at c0a00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: iwlwifi

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
    Subsystem: Toshiba America Info Systems Device fb30
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

``````

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:88:e3:1c:40:03
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.84 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c0b04000-c0b04fff memory:c0b00000-c0b03fff
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c0a00000-c0a01fff

```Thank inadvance

---

### Post by xastey on 2013-02-09
Sorry to bump but does anyone have any pointers for addressing the other 2 problems, I've been searching over the forums and google but no luck so far

---

### Post by mind_exploit on 2013-02-11
Hey, man :)

I bought the same one, 3 months ago, and the brightness doesn't work for me too. Tried many distros ... both installing and from live CDs.

SO - I had partial success (really partial) when I was on Kubuntu, and installed KGamma, so I was able to achieve some screen light changes. But as I understood - it's changing the gamma and not the brightness ... i.e. the colors, and not the hardware screen properties.
(I played a lot with those options you add in the /etc/default/grub file, I don't remember the exact ones that were there when I managed to do that ... but I think they were
```
acpi_osi=linux acpi_backlight=vendor
``` ...)

So, two conclusions:

1. Still searching for distro that will be able to do this. I intend to try some bleeding-edge ones - like Arch or Gentoo - cause they have much more recent versions of the packages, so I hope that thanks to some of the changes and/or new features in them - this problem will go away.

2. This was my fourth Toshiba laptop, and I think that it will be the last one from this brand!!! I'll choose a more linux-compatible one, and will stop give money for Windows I don't want to use, and pay to a company that makes federos to MicroSoft!!! ... 

;)

PS: Please, let me know if you've fixed this :) ...

---

### Post by mind_exploit on 2013-09-12
Last month the NVidia driver updated itself, to version 319.20 ... and  I'm able to change the brightness of the screen. (The function keys are  not working still, but the slider from the battery monitor is perfect [IMG]http://forums.computers.toshiba-europe.com/forums/images/emoticons/happy.gif[/IMG] ... )

(phew)

---

