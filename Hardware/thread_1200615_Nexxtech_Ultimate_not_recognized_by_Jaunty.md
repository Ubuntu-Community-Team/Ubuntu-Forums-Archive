---
title: "Nexxtech Ultimate not recognized by Jaunty"
date: 2009-06-30
forum: Hardware
---

### Post by cdshamwell on 2009-06-30
I'm a n00b trying to figure out how to connect my wireless mouse.  If there is a forum I could be directed to that might assist me, I'd be greatly appreciative.  As it stands, I've spent a few hours searching forums and to no avail.  My wireless mouse is not recognized no matter which port I plug it into.

---

### Post by Sandlst on 2009-06-30
I don't use a wireless mouse, but I'm guessing the one you are using has a transmitter plugging into a usb slot?  One thing you might try is to plug the transmitter in, then run the command ```
dmesg
```in a terminal.  The last few lines should hopefully give more information on the problem, or maybe even a helpful error message.  Finding out the model number of the mouse (it usually is somewhere on the bottom) would help narrow your searches down, leading to better results.  Sorry I don't know of another specific forum that would help you out.  Good luck!

---

### Post by cdshamwell on 2009-06-30
Here's the lsusb printout

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1bcf:0535 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

looks like its found under sunplus now what

---

### Post by Sandlst on 2009-06-30
I'm guessing since you omitted the dmesg output that it contained no useful information, which is troublesome.  A quick search for sunplus innovation technology yields nothing useful either. Try unplugging the mouse, then plugging it back in and checking the system log with ```
cat /var/log/syslog
```Also please try ```
xinput list
```Once again, it is the last few lines that should be of interest.  I think this thread should be moved to 'Hardware & Laptops' in order to be noticed by more people, and also because I'm pretty sure this section is meant for networking problems only.  You can report the post to request it be moved via the icon under your name.  Good luck!

---

### Post by cdshamwell on 2009-06-30
I moved it, it's got the same name and everything and ALL the info you wanted, including the dmesg

---

### Post by cdshamwell on 2009-06-30
I'm a n00b trying to figure out how to connect my wireless mouse. If there is a forum I could be directed to that might assist me, I'd be greatly appreciative. As it stands, I've spent a few hours searching forums and to no avail. My wireless mouse is not recognized no matter which port I plug it into.

dmesg output:

[    0.656115] ACPI: (supports S0 S3 S4 S5)
[    0.656153] ACPI: Using IOAPIC for interrupt routing
[    0.658051] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.695247] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.695254] ACPI: EC: driver started in interrupt mode
[    0.695541] ACPI: No dock devices found.
[    0.695564] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.695696] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0500000-0xf057ffff]
[    0.695705] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.695714] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.695722] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf0600000-0xf063ffff]
[    0.695763] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0580000-0xf05fffff]
[    0.695900] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0640000-0xf0643fff]
[    0.695953] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.695961] pci 0000:00:1b.0: PME# disabled
[    0.696055] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.696063] pci 0000:00:1c.0: PME# disabled
[    0.696152] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.696160] pci 0000:00:1c.1: PME# disabled
[    0.696243] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.696250] pci 0000:00:1c.2: PME# disabled
[    0.696334] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.696414] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.696491] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.696567] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.696648] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0844000-0xf08443ff]
[    0.696708] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.696716] pci 0000:00:1d.7: PME# disabled
[    0.696891] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.696899] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.696943] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.696955] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.696967] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.696978] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.696991] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.697057] pci 0000:00:1f.2: reg 10 io port: [0x18c8-0x18cf]
[    0.697069] pci 0000:00:1f.2: reg 14 io port: [0x18c0-0x18c3]
[    0.697081] pci 0000:00:1f.2: reg 18 io port: [0x18a8-0x18af]
[    0.697092] pci 0000:00:1f.2: reg 1c io port: [0x180c-0x180f]
[    0.697104] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.697115] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf0844400-0xf08447ff]
[    0.697141] pci 0000:00:1f.2: PME# supported from D3hot
[    0.697148] pci 0000:00:1f.2: PME# disabled
[    0.697216] pci 0000:00:1f.3: reg 20 io port: [0x18e0-0x18ff]
[    0.697480] pci 0000:02:00.0: reg 10 64bit mmio: [0xf0200000-0xf020ffff]
[    0.697615] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.697629] pci 0000:02:00.0: PME# disabled
[    0.697731] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.697740] pci 0000:00:1c.0: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    0.697752] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf00fffff]
[    0.697825] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.697833] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    0.697845] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0100000-0xf01fffff]
[    0.698220] pci 0000:05:00.0: reg 10 64bit mmio: [0xf0400000-0xf0403fff]
[    0.698354] pci 0000:05:00.0: supports D1 D2
[    0.698359] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.698373] pci 0000:05:00.0: PME# disabled
[    0.698506] pci 0000:00:1c.2: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    0.698581] pci 0000:00:1e.0: transparent bridge
[    0.698629] bus 00 -> node 0
[    0.698643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.699360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.699643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.699924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.700247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.715028] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.715266] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.715506] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.715738] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.715972] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.716221] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.716460] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.716693] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.717087] ACPI: WMI: Mapper loaded
[    0.717205] SCSI subsystem initialized
[    0.717205] libata version 3.00 loaded.
[    0.717205] usbcore: registered new interface driver usbfs
[    0.717205] usbcore: registered new interface driver hub
[    0.717205] usbcore: registered new device driver usb
[    0.717205] PCI: Using ACPI for IRQ routing
[    0.724039] Bluetooth: Core ver 2.13
[    0.724107] NET: Registered protocol family 31
[    0.724107] Bluetooth: HCI device and connection manager initialized
[    0.724107] Bluetooth: HCI socket layer initialized
[    0.724107] NET: Registered protocol family 8
[    0.724107] NET: Registered protocol family 20
[    0.724163] NetLabel: Initializing
[    0.724168] NetLabel:  domain hash size = 128
[    0.724172] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.724198] NetLabel:  unlabeled traffic allowed by default
[    0.724231] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.724240] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.728114] AppArmor: AppArmor Filesystem Enabled
[    0.732035] Switched to high resolution mode on CPU 0
[    0.732332] Switched to high resolution mode on CPU 1
[    0.736090] pnp: PnP ACPI init
[    0.736164] ACPI: bus type pnp registered
[    0.745819] pnp: PnP ACPI: found 10 devices
[    0.745824] ACPI: ACPI bus type pnp unregistered
[    0.745831] PnPBIOS: Disabled by ACPI PNP
[    0.745852] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.745859] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.745866] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.745872] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.745878] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.745884] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.745891] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.745897] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.745911] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.745924] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.745930] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.745936] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.745942] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.745948] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.745954] system 00:05: ioport range 0x380-0x384 has been reserved
[    0.745959] system 00:05: ioport range 0x386-0x387 has been reserved
[    0.745970] system 00:06: ioport range 0x6a0-0x6af has been reserved
[    0.745976] system 00:06: ioport range 0x6b0-0x6ff has been reserved
[    0.780902] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.780911] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.780922] pci 0000:00:1c.0:   MEM window: 0xf0200000-0xf02fffff
[    0.780930] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
[    0.780942] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.780949] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.780959] pci 0000:00:1c.1:   MEM window: 0xf0300000-0xf03fffff
[    0.780967] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0100000-0x000000f01fffff
[    0.780979] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.780984] pci 0000:00:1c.2:   IO window: disabled
[    0.780993] pci 0000:00:1c.2:   MEM window: 0xf0400000-0xf04fffff
[    0.781001] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.781016] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.781022] pci 0000:00:1e.0:   IO window: disabled
[    0.781031] pci 0000:00:1e.0:   MEM window: disabled
[    0.781038] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.781067] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.781076] pci 0000:00:1c.0: setting latency timer to 64
[    0.781093] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.781101] pci 0000:00:1c.1: setting latency timer to 64
[    0.781117] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.781125] pci 0000:00:1c.2: setting latency timer to 64

---

### Post by cdshamwell on 2009-06-30
[    0.781137] pci 0000:00:1e.0: setting latency timer to 64
[    0.781145] bus: 00 index 0 io port: [0x00-0xffff]
[    0.781150] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.781155] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.781160] bus: 02 index 1 mmio: [0xf0200000-0xf02fffff]
[    0.781165] bus: 02 index 2 mmio: [0xf0000000-0xf00fffff]
[    0.781169] bus: 02 index 3 mmio: [0x0-0x0]
[    0.781174] bus: 03 index 0 io port: [0x3000-0x3fff]
[    0.781178] bus: 03 index 1 mmio: [0xf0300000-0xf03fffff]
[    0.781183] bus: 03 index 2 mmio: [0xf0100000-0xf01fffff]
[    0.781188] bus: 03 index 3 mmio: [0x0-0x0]
[    0.781192] bus: 05 index 0 mmio: [0x0-0x0]
[    0.781196] bus: 05 index 1 mmio: [0xf0400000-0xf04fffff]
[    0.781200] bus: 05 index 2 mmio: [0x0-0x0]
[    0.781204] bus: 05 index 3 mmio: [0x0-0x0]
[    0.781209] bus: 06 index 0 mmio: [0x0-0x0]
[    0.781213] bus: 06 index 1 mmio: [0x0-0x0]
[    0.781217] bus: 06 index 2 mmio: [0x0-0x0]
[    0.781221] bus: 06 index 3 io port: [0x00-0xffff]
[    0.781225] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.781245] NET: Registered protocol family 2
[    0.796273] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.796852] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.797688] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.798138] TCP: Hash tables configured (established 131072 bind 65536)
[    0.798145] TCP reno registered
[    0.804334] NET: Registered protocol family 1
[    0.804597] checking if image is initramfs... it is
[    1.816258] Freeing initrd memory: 7605k freed
[    1.816342] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.816348] Simple Boot Flag at 0x36 set to 0x1
[    1.816684] cpufreq: No nForce2 chipset.
[    1.816958] audit: initializing netlink socket (disabled)
[    1.816996] type=2000 audit(1246399423.816:1): initialized
[    1.831497] highmem bounce pool size: 64 pages
[    1.831509] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.834338] VFS: Disk quotas dquot_6.5.1
[    1.834462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.835803] fuse init (API version 7.10)
[    1.835987] msgmni has been set to 1698
[

---

### Post by cdshamwell on 2009-06-30
[   13.056715] usbcore: registered new interface driver uvcvideo
[   13.057121] USB Video Class driver (v0.1.0)
[   13.200554] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.289462] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.289620] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.405067] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   14.508085] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   33.462901] lp: driver loaded but no devices found
[   33.659406] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   34.250066] EXT3 FS on sda1, internal journal
[   35.690882] type=1505 audit(1246399458.617:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2124
[   35.803567] type=1505 audit(1246399458.729:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2128
[   35.803840] type=1505 audit(1246399458.729:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2128
[   35.803959] type=1505 audit(1246399458.729:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2128
[   35.804093] type=1505 audit(1246399458.733:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2128
[   35.890441] type=1505 audit(1246399458.817:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2133
[   36.208725] type=1505 audit(1246399459.137:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2137
[   36.209153] type=1505 audit(1246399459.137:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2137
[   36.273671] type=1505 audit(1246399459.201:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2141
[   42.098952] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.098962] Bluetooth: BNEP filters: protocol multicast
[   42.131435] Bridge firewalling registered
[   43.674293] ppdev: user-space parallel port driver
[   45.076522] [drm] Initialized drm 1.1.0 20060810
[   45.115398] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   45.115408] pci 0000:00:02.0: setting latency timer to 64
[   45.115726] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   45.120774] [drm:i915_setparam] *ERROR* unknown parameter 4
[   45.120854] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   46.670213] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   47.073765] tg3 0000:02:00.0: irq 2300 for MSI/MSI-X
[   47.141773] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.408047] eth1: no IPv6 routers present
[   75.982356] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   85.417502] ACPI: EC: GPE storm detected, transactions will use polling mode
[  162.097116] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 1338.124290] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1553.289386] [drm:i915_getparam] *ERROR* Unknown parameter 6

---

### Post by cdshamwell on 2009-06-30
Here's the lsusb printout

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1bcf:0535 Sunplus Innovation Technology Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by cdshamwell on 2009-06-30
cat /var/log/syslog


ad-only data: 1524k
Jun 30 18:04:21 shammobile kernel: [    3.592936] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Jun 30 18:04:21 shammobile kernel: [    3.743638] compcache: Compressed swap size set to: 513164 KB
Jun 30 18:04:21 shammobile kernel: [    3.744639] TLSF: pool: f7d85000, init_size=16384, max_size=0, grow_size=16384
Jun 30 18:04:21 shammobile kernel: [    3.861073] usb 1-3: new high speed USB device using ehci_hcd and address 3
Jun 30 18:04:21 shammobile kernel: [    4.148541] tg3.c:v3.94 (August 14, 2008)
Jun 30 18:04:21 shammobile kernel: [    4.148617] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 30 18:04:21 shammobile kernel: [    4.148642] tg3 0000:02:00.0: setting latency timer to 64
Jun 30 18:04:21 shammobile kernel: [    4.169723] usb 1-3: configuration #1 chosen from 1 choice
Jun 30 18:04:21 shammobile kernel: [    4.312307] usb 1-5: new high speed USB device using ehci_hcd and address 4
Jun 30 18:04:21 shammobile kernel: [    4.462386] usb 1-5: configuration #1 chosen from 1 choice
Jun 30 18:04:21 shammobile kernel: [    4.475686] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:23:8b:27:37:12
Jun 30 18:04:21 shammobile kernel: [    4.475698] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
Jun 30 18:04:21 shammobile kernel: [    4.475707] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun 30 18:04:21 shammobile kernel: [    4.553667] Adding 513160k swap on /dev/ramzswap0.  Priority:100 extents:1 across:513160k
Jun 30 18:04:21 shammobile kernel: [    4.660311] Initializing USB Mass Storage driver...
Jun 30 18:04:21 shammobile kernel: [    4.662096] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 30 18:04:21 shammobile kernel: [    4.662711] usbcore: registered new interface driver usb-storage
Jun 30 18:04:21 shammobile kernel: [    4.662720] USB Mass Storage support registered.
Jun 30 18:04:21 shammobile kernel: [    4.664078] usb-storage: device found at 4
Jun 30 18:04:21 shammobile kernel: [    4.664086] usb-storage: waiting for device to settle before scanning
Jun 30 18:04:21 shammobile kernel: [    4.712070] usb 2-2: new low speed USB device using uhci_hcd and address 2
Jun 30 18:04:21 shammobile kernel: [    4.737638] PM: Starting manual resume from disk
Jun 30 18:04:21 shammobile kernel: [    4.737647] PM: Resume from partition 8:5
Jun 30 18:04:21 shammobile kernel: [    4.737650] PM: Checking hibernation image.
Jun 30 18:04:21 shammobile kernel: [    4.737952] PM: Resume from disk failed.
Jun 30 18:04:21 shammobile kernel: [    4.788562] kjournald starting.  Commit interval 5 seconds
Jun 30 18:04:21 shammobile kernel: [    4.788601] EXT3-fs: mounted filesystem with ordered data mode.
Jun 30 18:04:21 shammobile kernel: [    4.884368] usb 2-2: configuration #1 chosen from 1 choice
Jun 30 18:04:21 shammobile kernel: [    9.660842] usb-storage: device scan complete
Jun 30 18:04:21 shammobile kernel: [    9.663161] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jun 30 18:04:21 shammobile kernel: [    9.666196] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jun 30 18:04:21 shammobile kernel: [    9.666397] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jun 30 18:04:21 shammobile kernel: [   11.580130] udev: starting version 141
Jun 30 18:04:21 shammobile kernel: [   11.851090] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
Jun 30 18:04:21 shammobile kernel: [   11.873201] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jun 30 18:04:21 shammobile kernel: [   11.891923] Linux agpgart interface v0.103
Jun 30 18:04:21 shammobile kernel: [   11.937715] usbcore: registered new interface driver hiddev
Jun 30 18:04:21 shammobile kernel: [   11.960688] input: 2.4GHz 2way RF Mouse Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7
Jun 30 18:04:21 shammobile kernel: [   12.004844] generic-usb 0003:1BCF:0535.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [2.4GHz 2way RF Mouse Receiver] on usb-0000:00:1d.0-2/input0
Jun 30 18:04:21 shammobile kernel: [   12.004918] usbcore: registered new interface driver usbhid
Jun 30 18:04:21 shammobile kernel: [   12.005004] usbhid: v2.6:USB HID core driver
Jun 30 18:04:21 shammobile kernel: [   12.267972] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Jun 30 18:04:21 shammobile kernel: [   12.268515] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Jun 30 18:04:21 shammobile kernel: [   12.271461] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000

---

### Post by cdshamwell on 2009-06-30
Jun 30 18:04:21 shammobile kernel: [   12.517884] intel_rng: FWH not detected
Jun 30 18:04:21 shammobile kernel: [   12.730833] Linux video capture interface: v2.00
Jun 30 18:04:21 shammobile kernel: [   12.808885] ieee80211_crypt: registered algorithm 'NULL'
Jun 30 18:04:21 shammobile kernel: [   12.814366] wl: module license 'MIXED/Proprietary' taints kernel.
Jun 30 18:04:21 shammobile kernel: [   12.819607] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 30 18:04:21 shammobile kernel: [   12.819629] wl 0000:05:00.0: setting latency timer to 64
Jun 30 18:04:21 shammobile kernel: [   12.991070] ieee80211_crypt: registered algorithm 'TKIP'
Jun 30 18:04:21 shammobile kernel: [   12.993152] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Jun 30 18:04:21 shammobile kernel: [   13.020644] iTCO_vendor_support: vendor-support=0
Jun 30 18:04:21 shammobile kernel: [   13.033524] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Jun 30 18:04:21 shammobile kernel: [   13.034005] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
Jun 30 18:04:21 shammobile kernel: [   13.034199] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 30 18:04:21 shammobile kernel: [   13.045210] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0241)
Jun 30 18:04:21 shammobile kernel: [   13.050059] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input8
Jun 30 18:04:21 shammobile kernel: [   13.056715] usbcore: registered new interface driver uvcvideo
Jun 30 18:04:21 shammobile kernel: [   13.057121] USB Video Class driver (v0.1.0)
Jun 30 18:04:21 shammobile kernel: [   13.200554] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Jun 30 18:04:21 shammobile kernel: [   13.289462] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 30 18:04:21 shammobile kernel: [   13.289620] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 30 18:04:21 shammobile kernel: [   14.405067] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
Jun 30 18:04:21 shammobile kernel: [   14.508085] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Jun 30 18:04:21 shammobile kernel: [   33.462901] lp: driver loaded but no devices found
Jun 30 18:04:21 shammobile kernel: [   33.659406] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
Jun 30 18:04:21 shammobile kernel: [   34.250066] EXT3 FS on sda1, internal journal
Jun 30 18:04:21 shammobile kernel: [   35.690882] type=1505 audit(1246399458.617:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2124
Jun 30 18:04:21 shammobile kernel: [   35.803567] type=1505 audit(1246399458.729:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2128
Jun 30 18:04:21 shammobile kernel: [   35.803840] type=1505 audit(1246399458.729:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2128
Jun 30 18:04:21 shammobile kernel: [   35.803959] type=1505 audit(1246399458.729:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2128
Jun 30 18:04:21 shammobile kernel: [   35.804093] type=1505 audit(1246399458.733:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2128
Jun 30 18:04:21 shammobile kernel: [   35.890441] type=1505 audit(1246399458.817:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2133
Jun 30 18:04:21 shammobile kernel: [   36.208725] type=1505 audit(1246399459.137:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2137
Jun 30 18:04:21 shammobile kernel: [   36.209153] type=1505 audit(1246399459.137:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2137
Jun 30 18:04:21 shammobile kernel: [   36.273671] type=1505 audit(1246399459.201:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2141
Jun 30 18:04:24 shammobile acpid: client connected from 2809[111:120] 
Jun 30 18:04:24 shammobile bluetoothd[2822]: Bluetooth daemon
Jun 30 18:04:24 shammobile bluetoothd[2822]: Starting SDP server
Jun 30 18:04:25 shammobile kernel: [   42.098952] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 30 18:04:25 shammobile kernel: [   42.098962] Bluetooth: BNEP filters: protocol multicast
Jun 30 18:04:25 shammobile kernel: [   42.131435] Bridge firewalling registered
Jun 30 18:04:25 shammobile bluetoothd[2822]: bridge pan0 created
Jun 30 18:04:25 shammobile bluetoothd[2822]: Registered interface org.bluez.Service on path /org/bluez/2822/any
Jun 30 18:04:25 shammobile bluetoothd[2822]: Starting experimental netlink support
Jun 30 18:04:25 shammobile bluetoothd[2822]: Failed to find Bluetooth netlink family
Jun 30 18:04:26 shammobile NetworkManager: <info>  starting... 
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_23_8b_27_37_12 
Jun 30 18:04:26 shammobile acpid: client connected from 2866[0:0] 
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth1): driver does not support SSID scans (scan_capa 0x00). 
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl') 
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_4d_dd_dc_65 
Jun 30 18:04:26 shammobile NetworkManager: <info>  Trying to start the supplicant... 
Jun 30 18:04:26 shammobile NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Successfully dropped root privileges.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: avahi-daemon 0.6.23 starting up.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Successfully called chroot().
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Successfully dropped remaining capabilities.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: No service file found in /etc/avahi/services.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Network interface enumeration completed.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Registering new address record for fe80::223:4dff:fedd:dc65 on eth1.*.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Server startup complete. Host name is shammobile.local. Local service cookie is 1898731448.
Jun 30 18:04:26 shammobile avahi-daemon[2913]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 30 18:04:26 shammobile nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_8b_27_37_12, iface: eth0): not well known
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_4d_dd_dc_65, iface: eth1): not well known
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 30 18:04:26 shammobile nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 30 18:04:26 shammobile nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: (168044344) ... get_connections.
Jun 30 18:04:26 shammobile nm-system-settings:    SCPlugin-Ifupdown: (168044344) ... get_connections (managed=false): return empty list.
Jun 30 18:04:26 shammobile nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun 30 18:04:26 shammobile kernel: [   43.674293] ppdev: user-space parallel port driver
Jun 30 18:04:26 shammobile NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle 
Jun 30 18:04:27 shammobile anacron[3030]: Anacron 2.3 started on 2009-06-30
Jun 30 18:04:27 shammobile anacron[3030]: Normal exit (0 jobs run)
Jun 30 18:04:27 shammobile /usr/sbin/cron[3073]: (CRON) INFO (pidfile fd = 3)
Jun 30 18:04:27 shammobile /usr/sbin/cron[3074]: (CRON) STARTUP (fork ok)
Jun 30 18:04:27 shammobile /usr/sbin/cron[3074]: (CRON) INFO (Running @reboot jobs)

---

### Post by cdshamwell on 2009-06-30
Jun 30 18:04:28 shammobile kernel: [   45.076522] [drm] Initialized drm 1.1.0 20060810
Jun 30 18:04:28 shammobile kernel: [   45.115398] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 30 18:04:28 shammobile kernel: [   45.115408] pci 0000:00:02.0: setting latency timer to 64
Jun 30 18:04:28 shammobile kernel: [   45.115726] [drm] Initialized i915 1.6.0 20080730 on minor 0

[ Jun 30 18:04:28 shammobile kernel: [   45.120774] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun 30 18:04:28 shammobile kernel: [   45.120854] [drm:i915_getparam] *ERROR* Unknown parameter 6
Jun 30 18:04:29 shammobile kernel: [   46.670213] [drm:i915_getparam] *ERROR* Unknown parameter 6
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth0): bringing up device. 
Jun 30 18:04:30 shammobile kernel: [   47.073765] tg3 0000:02:00.0: irq 2300 for MSI/MSI-X
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth0): preparing device. 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 30 18:04:30 shammobile NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun 30 18:04:30 shammobile NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jun 30 18:04:30 shammobile kernel: [   47.141773] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth1): preparing device. 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jun 30 18:04:30 shammobile NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jun 30 18:04:30 shammobile NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready 
Jun 30 18:04:31 shammobile nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_23_8b_27_37_12
Jun 30 18:04:35 shammobile kernel: [   52.408047] eth1: no IPv6 routers present
Jun 30 18:04:47 shammobile gdm[2863]: pam_sm_authenticate: Called 
Jun 30 18:04:47 shammobile gdm[2863]: pam_sm_authenticate: username = [charles] 
Jun 30 18:04:47 shammobile gdm[2863]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun 30 18:04:49 shammobile gdm[3294]: Error attempting to open [/home/charles/.ecryptfs/wrapped-passphrase] for reading 
Jun 30 18:04:49 shammobile gdm[3294]: Error attempting to unwrap passphrase from file [/home/charles/.ecryptfs/wrapped-passphrase]; rc = [-5] 
Jun 30 18:04:49 shammobile gdm[3294]: Error adding passphrase key token to user session keyring; rc = [-5] 
Jun 30 18:04:49 shammobile console-kit-daemon[2564]: WARNING: Couldn't read /proc/2563/environ: Failed to open file '/proc/2563/environ': No such file or directory 
Jun 30 18:04:52 shammobile pulseaudio[3404]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Jun 30 18:04:58 shammobile x-session-manager[3309]: Gtk-WARNING: Unable to locate theme engine in module_path: "aurora", 
Jun 30 18:04:58 shammobile kernel: [   75.982356] [drm:i915_getparam] *ERROR* Unknown parameter 6
Jun 30 18:05:02 shammobile x-session-manager[3309]: WARNING: Could not launch application 'awn.desktop': Unable to start application: Failed to execute child process "awn-autostart" (No such file or directory) 
Jun 30 18:05:02 shammobile x-session-manager[3309]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory) 
Jun 30 18:05:02 shammobile x-session-manager[3309]: WARNING: Could not launch application 'ggl-qt.desktop': Unable to start application: Failed to execute child process "/usr/bin/ggl-qt" (No such file or directory) 
Jun 30 18:05:08 shammobile kernel: [   85.417502] ACPI: EC: GPE storm detected, transactions will use polling mode
Jun 30 18:05:10 shammobile anacron[3618]: Anacron 2.3 started on 2009-06-30
Jun 30 18:05:10 shammobile anacron[3618]: Normal exit (0 jobs run)
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) starting connection 'Auto ShamFam' 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto ShamFam' has security, but secrets are required. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto ShamFam' has security, and secrets exist.  No new secrets needed. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Config: added 'ssid' value 'ShamFam' 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jun 30 18:05:11 shammobile NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 30 18:05:11 shammobile NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 30 18:05:11 shammobile NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 30 18:05:11 shammobile NetworkManager: <info>  Config: set interface ap_scan to 1 
Jun 30 18:05:11 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning 
Jun 30 18:05:16 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Jun 30 18:05:17 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Jun 30 18:05:17 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Jun 30 18:05:17 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake 
Jun 30 18:05:17 shammobile NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed 
Jun 30 18:05:17 shammobile NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ShamFam'. 
Jun 30 18:05:17 shammobile NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 30 18:05:17 shammobile NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun 30 18:05:17 shammobile NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jun 30 18:05:17 shammobile NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jun 30 18:05:18 shammobile NetworkManager: <info>  dhclient started with pid 3676 
Jun 30 18:05:18 shammobile NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun 30 18:05:18 shammobile dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jun 30 18:05:18 shammobile dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jun 30 18:05:18 shammobile dhclient: All rights reserved.
Jun 30 18:05:18 shammobile dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 30 18:05:18 shammobile dhclient: 
Jun 30 18:05:18 shammobile NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
Jun 30 18:05:18 shammobile dhclient: Listening on LPF/eth1/00:23:4d:dd:dc:65
Jun 30 18:05:18 shammobile dhclient: Sending on   LPF/eth1/00:23:4d:dd:dc:65
Jun 30 18:05:18 shammobile dhclient: Sending on   Socket/fallback
Jun 30 18:05:18 shammobile dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 30 18:05:19 shammobile dhclient: DHCPOFFER of 192.168.1.3 from 192.168.1.1
Jun 30 18:05:19 shammobile dhclient: DHCPREQUEST of 192.168.1.3 on eth1 to 255.255.255.255 port 67
Jun 30 18:05:19 shammobile dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Jun 30 18:05:19 shammobile NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jun 30 18:05:19 shammobile NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun 30 18:05:19 shammobile NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jun 30 18:05:19 shammobile NetworkManager: <info>    address 192.168.1.3 
Jun 30 18:05:19 shammobile NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jun 30 18:05:19 shammobile NetworkManager: <info>    gateway 192.168.1.1 
Jun 30 18:05:19 shammobile NetworkManager: <info>    nameserver '192.168.1.1' 
Jun 30 18:05:19 shammobile NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun 30 18:05:19 shammobile NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jun 30 18:05:19 shammobile NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jun 30 18:05:19 shammobile avahi-daemon[2913]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.3.
Jun 30 18:05:19 shammobile avahi-daemon[2913]: New relevant interface eth1.IPv4 for mDNS.
Jun 30 18:05:19 shammobile avahi-daemon[2913]: Registering new address record for 192.168.1.3 on

---

### Post by cdshamwell on 2009-06-30
[   11.937715] usbcore: registered new interface driver hiddev
[   11.960688] input: 2.4GHz 2way RF Mouse Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7
[   12.004844] generic-usb 0003:1BCF:0535.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [2.4GHz 2way RF Mouse Receiver] on usb-0000:00:1d.0-2/input0
[   12.004918] usbcore: registered new interface driver usbhid
[   12.005004] usbhid: v2.6:USB HID core driver
[   12.267972] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   12.268515] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   12.271461] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.517884] intel_rng: FWH not detected
[   12.730833] Linux video capture interface: v2.00
[   12.808885] ieee80211_crypt: registered algorithm 'NULL'
[   12.814366] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.819607] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.819629] wl 0000:05:00.0: setting latency timer to 64
[   12.991070] ieee80211_crypt: registered algorithm 'TKIP'
[   12.993152] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   13.020644] iTCO_vendor_support: vendor-support=0
[   13.033524] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.034005] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   13.034199] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.045210] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0241)
[   13.050059] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input8
 eth1.IPv4.
Jun 30 18:05:19 shammobile dhclient: bound to 192.168.1.3 -- renewal in 43118 seconds.
Jun 30 18:05:20 shammobile NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jun 30 18:05:20 shammobile NetworkManager: <info>  Policy set 'Auto ShamFam' (eth1) as default for routing and DNS. 
Jun 30 18:05:20 shammobile NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jun 30 18:05:20 shammobile NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 30 18:05:22 shammobile ntpdate[3757]: adjust time server 91.189.94.4 offset -0.196646 sec
Jun 30 18:06:25 shammobile kernel: [  162.097116] ACPI: EC: missing confirmations, switch off interrupt mode.
Jun 30 18:10:01 shammobile /USR/SBIN/CRON[3926]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 18:11:26 shammobile sudo: pam_sm_authenticate: Called 
Jun 30 18:11:26 shammobile sudo: pam_sm_authenticate: username = [charles] 
Jun 30 18:11:26 shammobile sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun 30 18:11:27 shammobile sudo: Error attempting to open [/home/charles/.ecryptfs/wrapped-passphrase] for reading 
Jun 30 18:11:27 shammobile sudo: Error attempting to unwrap passphrase from file [/home/charles/.ecryptfs/wrapped-passphrase]; rc = [-5] 
Jun 30 18:11:27 shammobile sudo: Error adding passphrase key token to user session keyring; rc = [-5] 
Jun 30 18:17:01 shammobile /USR/SBIN/CRON[4258]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 30 18:20:01 shammobile /USR/SBIN/CRON[4324]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 18:26:01 shammobile kernel: [ 1338.124290] CE: hpet increasing min_delta_ns to 15000 nsec
Jun 30 18:29:36 shammobile kernel: [ 1553.289386] [drm:i915_getparam] *ERROR* Unknown parameter 6
Jun 30 18:30:01 shammobile /USR/SBIN/CRON[4465]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 18:40:01 shammobile /USR/SBIN/CRON[4605]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 18:50:01 shammobile /USR/SBIN/CRON[4744]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:00:01 shammobile /USR/SBIN/CRON[4890]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:00:01 shammobile /USR/SBIN/CRON[4891]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun 30 19:10:01 shammobile /USR/SBIN/CRON[5084]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:17:01 shammobile /USR/SBIN/CRON[5222]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 30 19:20:02 shammobile /USR/SBIN/CRON[5287]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:30:01 shammobile /USR/SBIN/CRON[5426]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:34:54 shammobile NetworkManager: <debug> [1246404894.007535] periodic_update(): Roamed from BSSID 00:22:3F:29:EE:A4 (ShamFam) to (none) ((none)) 
Jun 30 19:35:00 shammobile NetworkManager: <debug> [1246404900.008005] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:3F:29:EE:A4 (ShamFam) 
Jun 30 19:40:01 shammobile /USR/SBIN/CRON[5564]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 19:50:01 shammobile /USR/SBIN/CRON[5703]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 20:00:01 shammobile /USR/SBIN/CRON[5844]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 20:00:01 shammobile /USR/SBIN/CRON[5864]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun 30 20:10:02 shammobile /USR/SBIN/CRON[6030]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 20:17:01 shammobile /USR/SBIN/CRON[6168]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 30 20:20:01 shammobile /USR/SBIN/CRON[6233]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 20:30:01 shammobile /USR/SBIN/CRON[6371]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 30 20:39:13 shammobile anacron[6810]: Anacron 2.3 started on 2009-06-30
Jun 30 20:39:13 shammobile anacron[6810]: Normal exit (0 jobs run)
Jun 30 20:39:13 shammobile anacron[6893]: Anacron 2.3 started on 2009-06-30
Jun 30 20:39:13 shammobile anacron[6893]: Normal exit (0 jobs run)
Jun 30 20:40:01 shammobile /USR/SBIN/CRON[6976]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

### Post by cdshamwell on 2009-06-30
xinput list

"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Synaptics Touchpad"	id=2	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"2.4GHz 2way RF Mouse Receiver"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=7	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1



Sorry I'm a n00b and didn't know what was the important stuff.

---

### Post by Sandlst on 2009-06-30
> **cdshamwell said:**
> 
"2.4GHz 2way RF Mouse Receiver"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

It appears to me this is the most important section out of all the output.  The part that really concerns me is this line:> "2.4GHz 2way RF Mouse Receiver"	id=3	[XExtensionKeyboard]The touchpad is showing the equivalent line as > "SynPS/2 Synaptics TouchPad" id=7 [XExtensionPointer]
It almost seems that the system is detecting your mouse as a keyboard instead, which would stop it from working.  

This actually has happened to me before, although it was with a wired mouse, and another distro.  To test it, open up a blank document and move the connected mouse around, press buttons, etc.  If a bunch of garbage text types in, this is indeed the problem you are having.  Unfortunately, I was never able to fix the problem myself, despite several days trying to do so.  

If it happened to me again in Ubuntu, I would download other live-cds and see if I could find a distro that did work with the mouse correctly.  I would also head over to launchpad and file a bug about the problem.

Good luck!

---

### Post by cdshamwell on 2009-07-01
If i do get another version will i loose everything i have on my computer or is there a way to upgrade without losing what i have.

---

### Post by Sandlst on 2009-07-01
There is no easy way to back up installed programs when trying out a new distro.  I would try several live cds from different distros to see if any of them detects the mouse correctly, since obviously if none of them do there is no point in replacing ubuntu.  In the meantime, hopefully someone more knowledgeable than me will see this thread and offer a better solution; regardless I think you should report this as a bug on launchpad: if you have never reported a bug before you will have to create an account first.  The ubuntu section of lauchpad can be found here:

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

  When you make the bug report, make sure to add the outputs of the various commands in this thread.  Good luck!

---

