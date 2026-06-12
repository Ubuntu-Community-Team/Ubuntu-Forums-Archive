---
title: "Cannot access secondary gpu (Bumblebee, GT 740M)"
date: 2015-09-25
forum: Hardware
---

### Post by Geosearchef on 2015-09-25
Hello!

After installing Ubuntu on my laptop i tried to install a driver for my NVIDIA Geforce GT 740M. Sadly i wasn't able to do so.


```
ubuntu:~$ lspci | grep "VGA\|3D"
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
0a:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

```

I installed the version 319 of the driver in combination with bumblebee over apt-get.

Installed packages:

```
ubuntu:~$ dpkg --get-selections | grep -v deinstall | grep "bumblebee\|nvidia-\|bbswitch"
bbswitch-dkms                    install
bumblebee                    install
bumblebee-nvidia                install
nvidia-319                    install
nvidia-331                    install
nvidia-340                    install
nvidia-opencl-icd-340                install
nvidia-prime                    install
nvidia-settings                    install

```


If I use optirun to start a program i get this error:

```
[  901.661718] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.

[  901.661774] [ERROR]Aborting because fallback start is disabled.

```

While booting it also shows me the error: ```
ACPI PCC Probe failed
```


dmesg:

```
[    0.358189] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358246] pci 0000:09:00.0: System wakeup disabled by ACPI
[    0.369899] pci 0000:00:1c.3: PCI bridge to [bus 09]
[    0.369903] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.369906] pci 0000:00:1c.3:   bridge window [mem 0xb5400000-0xb54fffff]
[    0.369994] pci 0000:0a:00.0: [10de:1292] type 00 class 0x030200
[    0.370016] pci 0000:0a:00.0: reg 0x10: [mem 0xb3000000-0xb3ffffff]
[    0.370038] pci 0000:0a:00.0: reg 0x14: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.370059] pci 0000:0a:00.0: reg 0x1c: [mem 0xb0000000-0xb1ffffff 64bit pref]
[    0.370074] pci 0000:0a:00.0: reg 0x24: [io  0x3000-0x307f]
[    0.370088] pci 0000:0a:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.381907] pci 0000:00:1c.4: PCI bridge to [bus 0a]
[    0.381911] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.381914] pci 0000:00:1c.4:   bridge window [mem 0xb3000000-0xb3ffffff]
[    0.381919] pci 0000:00:1c.4:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.382593] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *7
[    0.382646] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.382695] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.382745] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.382793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.382842] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.382891] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.382939] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *7
[    0.383089] ACPI: Enabled 4 GPEs in block 00 to 7F
[    0.383145] ACPI : EC: GPE = 0x8, I/O: command/status = 0x66, data = 0x62
[    0.383251] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.383254] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.383258] vgaarb: loaded
[    0.383259] vgaarb: bridge control possible 0000:00:02.0
[    0.383547] SCSI subsystem initialized
[    0.383597] libata version 3.00 loaded.
[    0.383622] ACPI: bus type USB registered
[    0.383642] usbcore: registered new interface driver usbfs
[    0.383651] usbcore: registered new interface driver hub
[    0.383671] usbcore: registered new device driver usb
[    0.383822] PCI: Using ACPI for IRQ routing
[    0.389723] PCI: pci_cache_line_size set to 64 bytes
[    0.389828] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.389830] e820: reserve RAM buffer [mem 0x928af000-0x93ffffff]
[    0.389832] e820: reserve RAM buffer [mem 0x93000000-0x93ffffff]
[    0.389833] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    0.389963] NetLabel: Initializing
[    0.389965] NetLabel:  domain hash size = 128
[    0.389966] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.389979] NetLabel:  unlabeled traffic allowed by default
[    0.390040] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.390047] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.392085] Switched to clocksource hpet
[    0.398666] AppArmor: AppArmor Filesystem Enabled
[    0.398741] pnp: PnP ACPI init
[    0.399056] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.399060] system 00:00: [io  0xffff] has been reserved
[    0.399062] system 00:00: [io  0xffff] has been reserved
[    0.399064] system 00:00: [io  0xffff] has been reserved
[    0.399066] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.399068] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.399070] system 00:00: [io  0x0454-0x0457] has been reserved
[    0.399072] system 00:00: [io  0x0380-0x0387] has been reserved
[    0.399076] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.399129] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.399163] pnp 00:02: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    0.399203] pnp 00:03: Plug and Play ACPI device, IDs SYN1ea5 SYN1e00 SYN0002 PNP0f13 (active)
[    0.399422] pnp 00:04: disabling [mem 0xffffffff-0x100000ffe] because it overlaps 0000:0a:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.399445] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.399447] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.399450] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.399452] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.399454] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.399456] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.399458] system 00:04: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.399460] system 00:04: [mem 0xff000000-0xffffffff] could not be reserved
[    0.399462] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.399464] system 00:04: [mem 0x9fa10000-0x9fa10fff] has been reserved
[    0.399467] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.399751] pnp: PnP ACPI: found 5 devices
[    0.406084] pci 0000:0a:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
[    0.406096] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.406099] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.406101] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    0.406129] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.406131] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.406133] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.406138] pci 0000:00:1c.0: BAR 14: assigned [mem 0x9fb00000-0x9fcfffff]
[    0.406143] pci 0000:00:1c.0: BAR 15: assigned [mem 0x9fd00000-0x9fefffff 64bit pref]
[    0.406146] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.406149] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.406151] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.406156] pci 0000:00:1c.0:   bridge window [mem 0x9fb00000-0x9fcfffff]
[    0.406160] pci 0000:00:1c.0:   bridge window [mem 0x9fd00000-0x9fefffff 64bit pref]
[    0.406166] pci 0000:00:1c.1: PCI bridge to [bus 02-07]
[    0.406168] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.406173] pci 0000:00:1c.1:   bridge window [mem 0xb4000000-0xb4ffffff]
[    0.406176] pci 0000:00:1c.1:   bridge window [mem 0xb2000000-0xb2ffffff 64bit pref]
[    0.406182] pci 0000:00:1c.2: PCI bridge to [bus 08]
[    0.406186] pci 0000:00:1c.2:   bridge window [mem 0xb5500000-0xb55fffff]
[    0.406194] pci 0000:00:1c.3: PCI bridge to [bus 09]
[    0.406196] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.406201] pci 0000:00:1c.3:   bridge window [mem 0xb5400000-0xb54fffff]
[    0.406210] pci 0000:0a:00.0: BAR 6: no space for [mem size 0x00080000 pref]
[    0.406212] pci 0000:0a:00.0: BAR 6: failed to assign [mem size 0x00080000 pref]
[    0.406214] pci 0000:00:1c.4: PCI bridge to [bus 0a]
[    0.406216] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.406221] pci 0000:00:1c.4:   bridge window [mem 0xb3000000-0xb3ffffff]
[    0.406224] pci 0000:00:1c.4:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.406231] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.406233] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.406235] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.406237] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    0.406239] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.406240] pci_bus 0000:01: resource 1 [mem 0x9fb00000-0x9fcfffff]
[    0.406242] pci_bus 0000:01: resource 2 [mem 0x9fd00000-0x9fefffff 64bit pref]
[    0.406244] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.406246] pci_bus 0000:02: resource 1 [mem 0xb4000000-0xb4ffffff]
[    0.406248] pci_bus 0000:02: resource 2 [mem 0xb2000000-0xb2ffffff 64bit pref]
[    0.406250] pci_bus 0000:08: resource 1 [mem 0xb5500000-0xb55fffff]
[    0.406252] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.406254] pci_bus 0000:09: resource 1 [mem 0xb5400000-0xb54fffff]
[    0.406256] pci_bus 0000:0a: resource 0 [io  0x3000-0x3fff]
[    0.406257] pci_bus 0000:0a: resource 1 [mem 0xb3000000-0xb3ffffff]
[    0.406259] pci_bus 0000:0a: resource 2 [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.406291] NET: Registered protocol family 2
[    0.406509] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.406682] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.406828] TCP: Hash tables configured (established 65536 bind 65536)
[    0.406849] TCP: reno registered
[    0.406862] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.406894] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.406954] NET: Registered protocol family 1
[    0.406970] pci 0000:00:02.0: Video device with shadowed ROM
[    0.424281] PCI: CLS 64 bytes, default 64
[    0.424340] Trying to unpack rootfs image as initramfs...
[    0.814014] Freeing initrd memory: 19340K (ffff880035a2a000 - ffff880036d0d000)
[    0.814038] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.814041] software IO TLB [mem 0x8e8af000-0x928af000] (64MB) mapped at [ffff88008e8af000-ffff8800928aefff]
[    0.814080] Simple Boot Flag at 0x44 set to 0x1
[    0.814258] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.814318] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x14
[    0.814326] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x14
[    0.814335] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x14
[    0.814344] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x14
[    0.814397] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.814430] Scanning for low memory corruption every 60 seconds
[    0.814834] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.814861] Initialise system trusted keyring
[    0.814889] audit: initializing netlink subsys (disabled)
[    0.814902] audit: type=2000 audit(1443038400.796:1): initialized
[    0.815285] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.817036] zpool: loaded
[    0.817041] zbud: loaded
[    0.817227] VFS: Disk quotas dquot_6.5.2
[    0.817269] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.817796] fuse init (API version 7.23)
[    0.817958] Key type big_key registered
[    0.818348] Key type asymmetric registered
[    0.818352] Asymmetric key parser 'x509' registered
[    0.818393] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.818432] io scheduler noop registered
[    0.818436] io scheduler deadline registered (default)
[    0.818471] io scheduler cfq registered
[    0.819175] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.819193] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.819237] intel_idle: MWAIT substates: 0x11142120
[    0.819238] intel_idle: v0.4 model 0x45
[    0.819239] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.819843] ACPI: AC Adapter [ACAD] (on-line)
[    0.819950] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.820477] ACPI: Lid Switch [LID0]
[    0.820525] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.820529] ACPI: Power Button [PWRB]
[    0.820578] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.820580] ACPI: Power Button [PWRF]
[    0.821732] [Firmware Bug]: Invalid critical threshold (0)
[    0.823437] thermal LNXTHERM:00: registered as thermal_zone0
[    0.823439] ACPI: Thermal Zone [TZ01] (51 C)
[    0.823480] GHES: HEST is not enabled!
[    0.823612] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.825707] Linux agpgart interface v0.103
[    0.827083] brd: module loaded
[    0.827728] loop: module loaded
[    0.827967] libphy: Fixed MDIO Bus: probed
[    0.827970] tun: Universal TUN/TAP device driver, 1.6
[    0.827972] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.828017] PPP generic driver version 2.4.2
[    0.828188] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.828195] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.828274] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.828353] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.828355] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.828357] usb usb1: Product: xHCI Host Controller
[    0.828359] usb usb1: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.828360] usb usb1: SerialNumber: 0000:00:14.0
[    0.828488] hub 1-0:1.0: USB hub found
[    0.828500] hub 1-0:1.0: 9 ports detected
[    0.829044] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.829048] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.829081] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.829083] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.829085] usb usb2: Product: xHCI Host Controller
[    0.829086] usb usb2: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.829088] usb usb2: SerialNumber: 0000:00:14.0
[    0.829191] hub 2-0:1.0: USB hub found
[    0.829199] hub 2-0:1.0: 4 ports detected
[    0.829529] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.829535] ehci-pci: EHCI PCI platform driver
[    0.829651] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.829657] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.829668] ehci-pci 0000:00:1d.0: debug port 2
[    0.833587] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.833602] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb561c000
[    0.844462] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.844501] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.844503] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.844504] usb usb3: Product: EHCI Host Controller
[    0.844506] usb usb3: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
[    0.844508] usb usb3: SerialNumber: 0000:00:1d.0
[    0.844639] hub 3-0:1.0: USB hub found
[    0.844644] hub 3-0:1.0: 2 ports detected
[    0.844766] ehci-platform: EHCI generic platform driver
[    0.844776] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.844781] ohci-pci: OHCI PCI platform driver
[    0.844793] ohci-platform: OHCI generic platform driver
[    0.844801] uhci_hcd: USB Universal Host Controller Interface driver
[    0.844853] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.852479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.852485] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.852660] mousedev: PS/2 mouse device common for all mice
[    0.852892] rtc_cmos 00:01: RTC can wake from S4
[    0.853041] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.853069] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.853086] i2c /dev entries driver
[    0.853156] device-mapper: uevent: version 1.0.3
[    0.853249] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.853269] Intel P-state driver initializing.
[    0.853386] Consider also installing thermald for improved thermal control.
[    0.853393] ledtrig-cpu: registered to indicate activity on CPUs
[    0.853563] PCCT header not found.
[    0.853565] ACPI PCC probe failed.
[    0.853685] TCP: cubic registered
[    0.853790] NET: Registered protocol family 10
[    0.854033] NET: Registered protocol family 17
[    0.854044] Key type dns_resolver registered
[    0.854339] Loading compiled-in X.509 certificates
[    0.855226] Loaded X.509 cert 'Magrathea: Glacier signing key: 294dc012706f48b7cddf6374e2d79fe1b0609269'
[    0.855239] registered taskstats version 1
[    0.856783] Key type trusted registered
[    0.859280] Key type encrypted registered
[    0.859287] AppArmor: AppArmor sha1 policy hashing enabled
[    0.859291] ima: No TPM chip found, activating TPM-bypass!
[    0.859310] evm: HMAC attrs: 0x1
[    0.859761]   Magic number: 15:829:43
[    0.859846] rtc_cmos 00:01: setting system clock to 2015-09-23 20:00:01 UTC (1443038401)
[    0.859889] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.859890] EDD information not available.
[    0.859940] PM: Hibernation image not present or could not be loaded.
[    0.861000] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.882504] ACPI: Battery Slot [BAT0] (battery present)
[    0.882848] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.882850] Write protecting the kernel read-only data: 12288k
[    0.883093] Freeing unused kernel memory: 260K (ffff8800017bf000 - ffff880001800000)
[    0.883189] Freeing unused kernel memory: 340K (ffff880001bab000 - ffff880001c00000)
[    0.894178] systemd-udevd[119]: starting version 204
[    0.911813] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 41
[    0.913780] ahci 0000:00:1f.2: version 3.0
[    0.914062] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.914070] r8169 0000:09:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.922157] r8169 0000:09:00.0 eth0: RTL8106e at 0xffffc90010e9e000, a0:48:1c:16:b3:a2, XID 10900800 IRQ 43
[    0.928547] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl SATA mode
[    0.928553] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    0.929497] scsi host0: ahci
[    0.929644] scsi host1: ahci
[    0.929728] scsi host2: ahci
[    0.929809] scsi host3: ahci
[    0.929848] ata1: SATA max UDMA/133 abar m2048@0xb561b000 port 0xb561b100 irq 42
[    0.929850] ata2: SATA max UDMA/133 abar m2048@0xb561b000 port 0xb561b180 irq 42
[    0.929851] ata3: DUMMY
[    0.929852] ata4: DUMMY
[    1.140766] usb 1-1: new low-speed USB device number 2 using xhci_hcd
[    1.156773] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.248848] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.248869] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.250574] ata2.00: ATAPI: hp       DVDRAM GU70N, U703, max UDMA/100
[    1.250763] ata1.00: ATA-9: HGST HTS541010A9E680, JA0OA590, max UDMA/133
[    1.250768] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.252492] ata2.00: configured for UDMA/100
[    1.252835] ata1.00: configured for UDMA/133
[    1.253012] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS541010A9 A590 PQ: 0 ANSI: 5
[    1.253370] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.253375] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.253414] sd 0:0:0:0: [sda] Write Protect is off
[    1.253418] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.253429] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.253432] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.253930] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GU70N     U703 PQ: 0 ANSI: 5
[    1.270922] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.270926] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.271153] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.271267] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.289318] usb 3-1: New USB device found, idVendor=8087, idProduct=8000
[    1.289323] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.289605] hub 3-1:1.0: USB hub found
[    1.289803] hub 3-1:1.0: 8 ports detected
[    1.325818]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.326688] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.329995] usb 1-1: New USB device found, idVendor=413c, idProduct=2106
[    1.330008] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.330010] usb 1-1: Product: Dell QuietKey Keyboard
[    1.330011] usb 1-1: Manufacturer: DELL
[    1.330147] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.333344] hidraw: raw HID events driver (C) Jiri Kosina
[    1.336929] usbcore: registered new interface driver usbhid
[    1.336933] usbhid: USB HID core driver
[    1.338546] input: DELL Dell QuietKey Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:413C:2106.0001/input/input6
[    1.393103] hid-generic 0003:413C:2106.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL Dell QuietKey Keyboard] on usb-0000:00:14.0-1/input0
[    1.444955] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[    1.674697] usb 1-3: New USB device found, idVendor=05c8, idProduct=0361
[    1.674701] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.674703] usb 1-3: Product: HP Truevision HD
[    1.674705] usb 1-3: Manufacturer: SunplusIT INC.
[    1.797729] psmouse serio1: synaptics: queried max coordinates: x [..5696], y [..4884]
[    1.813264] tsc: Refined TSC clocksource calibration: 2394.456 MHz
[    1.832921] psmouse serio1: synaptics: queried min coordinates: x [1276..], y [1044..]
[    1.899972] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00133/0x240000/0xa2400, board id: 2665, fw id: 1458825
[    1.909343] usb 1-6: new low-speed USB device number 4 using xhci_hcd
[    1.943053] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.950639] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.041203] usb 1-6: New USB device found, idVendor=413c, idProduct=3012
[    2.041207] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.041209] usb 1-6: Product: Dell USB Optical Mouse
[    2.041211] usb 1-6: Manufacturer: Dell
[    2.041390] usb 1-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.043426] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:413C:3012.0002/input/input7
[    2.043826] hid-generic 0003:413C:3012.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:14.0-6/input0
[    2.429393] random: nonblocking pool is initialized
[    2.814167] Switched to clocksource tsc
[    3.092648] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.092658] init: plymouth-upstart-bridge main process ended, respawning
[    3.094649] init: plymouth-upstart-bridge main process (205) terminated with status 1
[    3.094663] init: plymouth-upstart-bridge main process ended, respawning
[    3.095886] init: plymouth-upstart-bridge main process (207) terminated with status 1
[    3.095893] init: plymouth-upstart-bridge main process ended, respawning
[    3.097479] init: plymouth-upstart-bridge main process (208) terminated with status 1
[    3.097486] init: plymouth-upstart-bridge main process ended, respawning
[    3.098610] init: plymouth-upstart-bridge main process (210) terminated with status 1
[    3.098617] init: plymouth-upstart-bridge main process ended, respawning
[    3.100299] init: plymouth-upstart-bridge main process (211) terminated with status 1
[    3.100308] init: plymouth-upstart-bridge main process ended, respawning
[    3.101618] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    3.101626] init: plymouth-upstart-bridge main process ended, respawning
[    3.103577] init: plymouth-upstart-bridge main process (214) terminated with status 1
[    3.103592] init: plymouth-upstart-bridge main process ended, respawning
[    3.105290] init: plymouth-upstart-bridge main process (216) terminated with status 1
[    3.105310] init: plymouth-upstart-bridge main process ended, respawning
[    3.106586] init: plymouth-upstart-bridge main process (217) terminated with status 1
[    3.106592] init: plymouth-upstart-bridge main process ended, respawning
[    3.107810] init: plymouth-upstart-bridge main process (219) terminated with status 1
[    3.107817] init: plymouth-upstart-bridge respawning too fast, stopped
[    4.073328] Adding 7999484k swap on /dev/sda2.  Priority:-1 extents:1 across:7999484k FS
[    4.800214] systemd-udevd[321]: starting version 204
[    5.617174] lp: driver loaded but no devices found
[    5.733314] ppdev: user-space parallel port driver
[    6.317127] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.261385] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    8.127871] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.132477] wmi: Mapper loaded
[    8.166487] hp_accel: laptop model unknown, using default axes configuration
[    8.174674] lis3lv02d: 8 bits 3DC sensor found
[    8.218509] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[    8.282998] Initializing HPQ6001 module
[    8.283070] input: HP Wireless hotkeys as /devices/virtual/input/input9
[    8.494571] [drm] Initialized drm 1.1.0 20060810
[    8.552443] cfg80211: Calling CRDA to update world regulatory domain
[    8.698212] media: Linux media interface: v0.10
[    8.717285] Linux video capture interface: v2.00
[    8.731235] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    8.731237] Copyright(c) 2003- 2014 Intel Corporation
[    8.731373] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    8.978129] input: HP WMI hotkeys as /devices/virtual/input/input10
[    9.028940] AVX2 version of gcm_enc/dec engaged.
[    9.028943] AES CTR mode by8 optimization enabled
[    9.055443] iwlwifi 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    9.120135] uvcvideo: Found UVC 1.00 device HP Truevision HD (05c8:0361)
[    9.128619] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input11
[    9.128717] usbcore: registered new interface driver uvcvideo
[    9.128720] USB Video Class driver (1.1.1)
[    9.178048] [drm] Memory usable by graphics device = 2048M
[    9.178052] [drm] Replacing VGA console driver
[    9.179136] Console: switching to colour dummy device 80x25
[    9.203271] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.203273] [drm] Driver supports precise vblank timestamp query.
[    9.203379] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.269013] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    9.269338] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    9.269343] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
[    9.269348] ACPI Error: Method parse/execution failed [\_SB_.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802568e29b0), AE_NOT_FOUND (20141107/psparse-536)
[    9.269408] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/LNXVIDEO:00/input/input12
[    9.270795] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.270937] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input13
[    9.270993] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    9.271125] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    9.294533] fbcon: inteldrmfb (fb0) is primary device
[    9.317211] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    9.317212] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.317213] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    9.317214] sound hdaudioC1D0:    mono: mono_out=0x0
[    9.317214] sound hdaudioC1D0:    inputs:
[    9.317215] sound hdaudioC1D0:      Mic=0x19
[    9.317216] sound hdaudioC1D0:      Internal Mic=0x12
[    9.324000] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[    9.324274] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[    9.324957] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
[    9.489551] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.489552] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.489552] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.489554] iwlwifi 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    9.489652] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[    9.624595] kvm: disabled by bios
[    9.648596] kvm: disabled by bios
[    9.649487] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.855690] cfg80211: World regulatory domain updated:
[    9.855692] cfg80211:  DFS Master region: unset
[    9.855692] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    9.855694] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    9.855696] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    9.855697] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    9.855697] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    9.855698] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.026708] intel_rapl: Found RAPL domain package
[   10.026710] intel_rapl: Found RAPL domain core
[   10.026711] intel_rapl: Found RAPL domain uncore
[   10.026713] intel_rapl: Found RAPL domain dram
[   10.229704] audit: type=1400 audit(1443038410.856:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=504 comm="apparmor_parser"
[   10.229709] audit: type=1400 audit(1443038410.856:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=504 comm="apparmor_parser"
[   10.229712] audit: type=1400 audit(1443038410.856:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=504 comm="apparmor_parser"
[   10.229948] audit: type=1400 audit(1443038410.856:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=505 comm="apparmor_parser"
[   10.229956] audit: type=1400 audit(1443038410.856:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=505 comm="apparmor_parser"
[   10.229961] audit: type=1400 audit(1443038410.856:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   10.229970] audit: type=1400 audit(1443038410.856:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=565 comm="apparmor_parser"
[   10.229976] audit: type=1400 audit(1443038410.856:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=565 comm="apparmor_parser"
[   10.229982] audit: type=1400 audit(1443038410.856:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=565 comm="apparmor_parser"
[   10.230137] audit: type=1400 audit(1443038410.856:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=504 comm="apparmor_parser"
[   10.388190] Console: switching to colour frame buffer device 160x48
[   10.393109] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.393110] i915 0000:00:02.0: registered panic notifier
[   10.869671] init: failsafe main process (590) killed by TERM signal
[   11.891540] init: avahi-cups-reload main process (791) terminated with status 1
[   12.702241] Bluetooth: Core ver 2.20
[   12.702253] NET: Registered protocol family 31
[   12.702254] Bluetooth: HCI device and connection manager initialized
[   12.702257] Bluetooth: HCI socket layer initialized
[   12.702259] Bluetooth: L2CAP socket layer initialized
[   12.702263] Bluetooth: SCO socket layer initialized
[   12.871594] Bluetooth: RFCOMM TTY layer initialized
[   12.871599] Bluetooth: RFCOMM socket layer initialized
[   12.871604] Bluetooth: RFCOMM ver 1.11
[   12.960064] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.960067] Bluetooth: BNEP filters: protocol multicast
[   12.960071] Bluetooth: BNEP socket layer initialized
[   15.178134] r8169 0000:09:00.0 eth0: link down
[   15.178156] r8169 0000:09:00.0 eth0: link down
[   15.178175] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.446191] init: smbd main process (656) killed by HUP signal
[   15.446198] init: smbd main process ended, respawning
[   15.539600] audit_printk_skb: 33 callbacks suppressed
[   15.539604] audit: type=1400 audit(1443038416.164:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=853 comm="apparmor_parser"
[   16.844267] audit: type=1400 audit(1443038417.464:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=901 comm="apparmor_parser"
[   16.844275] audit: type=1400 audit(1443038417.464:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[   16.844280] audit: type=1400 audit(1443038417.464:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   16.844698] audit: type=1400 audit(1443038417.464:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[   16.844702] audit: type=1400 audit(1443038417.464:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   16.844839] audit: type=1400 audit(1443038417.464:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   16.846377] audit: type=1400 audit(1443038417.468:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=905 comm="apparmor_parser"
[   16.848523] audit: type=1400 audit(1443038417.468:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=906 comm="apparmor_parser"
[   16.848527] audit: type=1400 audit(1443038417.468:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=906 comm="apparmor_parser"
[   17.510735] init: samba-ad-dc main process (839) terminated with status 1
[   21.248120] bbswitch: module verification failed: signature and/or  required key missing - tainting kernel
[   21.248395] bbswitch: version 0.8
[   21.248402] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   21.248410] bbswitch: Found discrete VGA device 0000:0a:00.0: \_SB_.PCI0.RP05.PEGP
[   21.248423] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   21.248514] bbswitch: detected an Optimus _DSM function
[   21.248531] pci 0000:0a:00.0: enabling device (0006 -> 0007)
[   21.248576] bbswitch: Succesfully loaded. Discrete card 0000:0a:00.0 is on
[   21.250658] bbswitch: disabling discrete graphics
[   21.250665] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   21.897869] r8169 0000:09:00.0 eth0: link up
[   21.897879] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  150.465475] bbswitch: enabling discrete graphics
[  151.238577] nvidia: module license 'NVIDIA' taints kernel.
[  151.238586] Disabling lock debugging due to kernel taint
[  151.258781] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:0a:00.0 on minor 1
[  151.258797] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.76  Thu Jan 22 12:11:08 PST 2015

```


As far as i was able to find out, this bug didn't occur befor kernel version 3.13. But I haven't tried yet. Any ideas how i could fix this?

---

### Post by Bashing-om on 2015-09-25
Geosearchef; Hello ;

I would think that what you have here is a conflict in controllers:
> 
bumblebee                    install
nvidia-prime                    install


Nvidia now offers their support to us for hybrid graphics . Though the implementation of nvidia-prime differs from that of the BumbleBee open source project, you may find using nvidia-prime the better option. But, nvidia-prime is different !

Purge the Nvida driver, and the controllers. Decide on which support platform you prefer and we advise on how to make that happen.

[INDENT][INDENT]keep in mind;
[INDENT][INDENT][INDENT]can not beat the Manufacturer for know-how
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Geosearchef on 2015-09-25
Thanks for helping!!

I think nvidia-prime actually is a better idea. I've also gotten some issues in graphically lightweight applications, maybe this will help, too.
So I'll just purge bumblebee, bbswitch and all nvidia drivers.
Afterwards just install nvidia-340 and nvidia-prime?

---

### Post by Bashing-om on 2015-09-25
Geosearchef; Yeah;

Something along those lines, but simpler and to the point:
```

sudo apt-get purge bumble*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get purge nvidia*
sudo ubuntu-drivers autoinstall
sudo nvidia-xconfig

```
How about we see what the system finds for a driver, and have the system install what it thinks is best ?
When the system installs the Nvidia driver it will also auto-install nvidia-prime. no fuss no muss no sweat.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]just keeps getting easier
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Geosearchef on 2015-09-26
I couldn't backup my xorg.conf cause there was none:

```
geosearchef@geosearchef-ubuntu:/etc/X11$ ls -al
total 108
drwxr-xr-x  11 root root  4096 Sep 24 17:30 .
drwxr-xr-x 145 root root 12288 Sep 26 13:33 ..
drwxr-xr-x   2 root root  4096 Aug  5 07:21 app-defaults
drwxr-xr-x   2 root root  4096 Aug  5 07:20 cursors
-rw-r--r--   1 root root    18 Aug  5 07:20 default-display-manager
drwxr-xr-x   4 root root  4096 Aug  5 07:18 fonts
-rw-r--r--   1 root root 17394 Dez  3  2009 rgb.txt
lrwxrwxrwx   1 root root    13 Sep 24 17:30 X -> /usr/bin/Xorg
drwxr-xr-x   2 root root  4096 Aug  5 07:21 xinit
drwxr-xr-x   2 root root  4096 Jan 15  2014 xkb
-rw-r--r--   1 root root   594 Sep 22 20:28 xorg.conf.09222015
-rw-r--r--   1 root root    86 Sep 23 23:06 xorg.conf.09232015
-rw-r--r--   1 root root   299 Sep 24 16:54 xorg.conf.09242015
-rw-r--r--   1 root root   270 Sep 22 20:28 xorg.conf.failsafe
-rwxr-xr-x   1 root root   709 Apr  1  2010 Xreset
drwxr-xr-x   2 root root  4096 Aug  5 07:19 Xreset.d
drwxr-xr-x   2 root root  4096 Aug  5 07:19 Xresources
-rwxr-xr-x   1 root root  3730 Okt  8  2014 Xsession
drwxr-xr-x   2 root root  4096 Aug  5 07:21 Xsession.d
-rw-r--r--   1 root root   265 Jul  1  2008 Xsession.options
drwxr-xr-x   2 root root  4096 Aug  5 07:21 xsm
-rw-r--r--   1 root root   601 Aug  5 07:19 Xwrapper.config
```


I purged bumblebee and all nvidia modules/drivers except for bbswitch.

```
geosearchef@geosearchef-ubuntu:~$ dpkg --get-selections | grep -v deinstall | grep "bumblebee\|nvidia-\|bbswitch"
bbswitch-dkms                    install
```


```
geosearchef@geosearchef-ubuntu:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcuda1-346 nvidia-opencl-icd-346 nvidia-prime nvidia-settings
The following packages will be REMOVED:
  libcuda1-340
The following NEW packages will be installed:
  libcuda1-346 nvidia-346 nvidia-opencl-icd-346 nvidia-prime nvidia-settings
0 upgraded, 5 newly installed, 1 to remove and 16 not upgraded.
```

```

geosearchef@geosearchef-ubuntu:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
```

So now I'm gonna reboot and test it out.

---

### Post by Geosearchef on 2015-09-26
I rebooted and am now able to change the used graphics card through nvidia-prime + relogging. It correctly detects the card and also uses it.
Sadly my performance is worse when using the dedicated card. Also it get's very hot so the fan is working full time at full power. I'll run a benchmark.

Also i get some errors:

```
[    8.262957] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.268765] hp_accel: laptop model unknown, using default axes configuration
[    8.274619] lis3lv02d: 8 bits 3DC sensor found
[    8.322498] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input9
[    8.357122] [drm] Initialized drm 1.1.0 20060810
[    8.721753] cfg80211: Calling CRDA to update world regulatory domain
[    9.041669] AVX2 version of gcm_enc/dec engaged.
[    9.041671] AES CTR mode by8 optimization enabled
[    9.157814] [drm] Memory usable by graphics device = 2048M
[    9.157816] [drm] Replacing VGA console driver
[    9.158889] Console: switching to colour dummy device 80x25
[    9.180439] input: HP WMI hotkeys as /devices/virtual/input/input10
[    9.183149] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.183151] [drm] Driver supports precise vblank timestamp query.
[    9.183261] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.224249] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    9.224251] Copyright(c) 2003- 2014 Intel Corporation
[    9.224379] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    9.260661] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    9.262304] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    9.262309] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
[    9.262313] ACPI Error: Method parse/execution failed [\_SB_.PCI0.RP05.PEGP.DD02._BCL] (Node ffff8802568e29b0), AE_NOT_FOUND (20141107/psparse-536)
[    9.262362] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/LNXVIDEO:00/input/input11
[    9.263772] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.263910] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input12
[    9.263996] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    9.287220] fbcon: inteldrmfb (fb0) is primary device
[    9.445700] media: Linux media interface: v0.10
[    9.549618] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    9.602709] iwlwifi 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    9.643530] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    9.643532] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.643533] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    9.643533] sound hdaudioC1D0:    mono: mono_out=0x0
[    9.643534] sound hdaudioC1D0:    inputs:
[    9.643535] sound hdaudioC1D0:      Mic=0x19
[    9.643536] sound hdaudioC1D0:      Internal Mic=0x12
[    9.647674] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[    9.650496] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[    9.650574] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[    9.654385] Linux video capture interface: v2.00
[    9.803178] kvm: disabled by bios
[   10.136831] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.136832] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.136833] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.136834] iwlwifi 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.136933] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[   10.169390] cfg80211: World regulatory domain updated:
[   10.169392] cfg80211:  DFS Master region: unset
[   10.169392] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.169394] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.169396] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.169397] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.169397] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.169398] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.182040] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.234570] uvcvideo: Found UVC 1.00 device HP Truevision HD (05c8:0361)
[   10.240054] intel_rapl: Found RAPL domain package
[   10.240056] intel_rapl: Found RAPL domain core
[   10.240057] intel_rapl: Found RAPL domain uncore
[   10.240059] intel_rapl: Found RAPL domain dram
[   10.242926] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input16
[   10.242989] usbcore: registered new interface driver uvcvideo
[   10.242990] USB Video Class driver (1.1.1)
[   10.396124] Console: switching to colour frame buffer device 160x48
[   10.400053] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.400055] i915 0000:00:02.0: registered panic notifier
[   10.565614] audit: type=1400 audit(1443268190.167:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=420 comm="apparmor_parser"
[   10.565621] audit: type=1400 audit(1443268190.167:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=420 comm="apparmor_parser"
[   10.565625] audit: type=1400 audit(1443268190.167:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=420 comm="apparmor_parser"
[   10.565902] audit: type=1400 audit(1443268190.167:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=509 comm="apparmor_parser"
[   10.565913] audit: type=1400 audit(1443268190.167:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=509 comm="apparmor_parser"
[   10.565919] audit: type=1400 audit(1443268190.167:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=509 comm="apparmor_parser"
[   10.565932] audit: type=1400 audit(1443268190.167:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=419 comm="apparmor_parser"
[   10.565940] audit: type=1400 audit(1443268190.167:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=419 comm="apparmor_parser"
[   10.565947] audit: type=1400 audit(1443268190.167:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=419 comm="apparmor_parser"
[   10.566051] audit: type=1400 audit(1443268190.167:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=420 comm="apparmor_parser"
[   11.538882] nvidia: module license 'NVIDIA' taints kernel.
[   11.538885] Disabling lock debugging due to kernel taint
[   11.541042] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   11.544195] nvidia 0000:0a:00.0: enabling device (0006 -> 0007)
[   11.544579] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:0a:00.0 on minor 1
[   11.544584] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.82  Wed Jun 17 10:37:46 PDT 2015
[   11.945359] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   12.714954] init: failsafe main process (669) killed by TERM signal
[   15.398734] init: avahi-cups-reload main process (756) terminated with status 1
[   15.745961] audit_printk_skb: 24 callbacks suppressed
[   15.745964] audit: type=1400 audit(1443268195.343:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=749 comm="apparmor_parser"
[   15.745970] audit: type=1400 audit(1443268195.343:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=749 comm="apparmor_parser"
[   15.746389] audit: type=1400 audit(1443268195.343:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=749 comm="apparmor_parser"
[   15.873441] Bluetooth: Core ver 2.20
[   15.873455] NET: Registered protocol family 31
[   15.873456] Bluetooth: HCI device and connection manager initialized
[   15.873460] Bluetooth: HCI socket layer initialized
[   15.873462] Bluetooth: L2CAP socket layer initialized
[   15.873468] Bluetooth: SCO socket layer initialized
[   16.121243] Bluetooth: RFCOMM TTY layer initialized
[   16.121249] Bluetooth: RFCOMM socket layer initialized
[   16.121253] Bluetooth: RFCOMM ver 1.11
[   17.343832] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.343834] Bluetooth: BNEP filters: protocol multicast
[   17.343837] Bluetooth: BNEP socket layer initialized
[   20.486305] r8169 0000:09:00.0 eth0: link down
[   20.486329] r8169 0000:09:00.0 eth0: link down
[   20.486352] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.703795] audit: type=1400 audit(1443268200.295:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   20.703802] audit: type=1400 audit(1443268200.295:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   20.703805] audit: type=1400 audit(1443268200.295:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   20.704059] audit: type=1400 audit(1443268200.295:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   20.704062] audit: type=1400 audit(1443268200.295:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   20.704195] audit: type=1400 audit(1443268200.295:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   20.889343] audit: type=1400 audit(1443268200.483:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=865 comm="apparmor_parser"
[   20.889440] audit: type=1400 audit(1443268200.483:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=853 comm="apparmor_parser"
[   20.892062] audit: type=1400 audit(1443268200.483:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=868 comm="apparmor_parser"
[   20.892068] audit: type=1400 audit(1443268200.483:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=868 comm="apparmor_parser"
[   20.892319] audit: type=1400 audit(1443268200.483:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=868 comm="apparmor_parser"
[   20.949435] audit: type=1400 audit(1443268200.543:34): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=871 comm="apparmor_parser"
[   20.969521] audit: type=1400 audit(1443268200.563:35): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=848 comm="apparmor_parser"
[   20.969528] audit: type=1400 audit(1443268200.563:36): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=848 comm="apparmor_parser"
[   20.969786] audit: type=1400 audit(1443268200.563:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=848 comm="apparmor_parser"
[   20.994538] audit: type=1400 audit(1443268200.587:38): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=852 comm="apparmor_parser"
[   21.460753] init: samba-ad-dc main process (789) terminated with status 1
[   22.213086] r8169 0000:09:00.0 eth0: link up
[   22.213094] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.551712] bbswitch: version 0.8
[   29.551719] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   29.551727] bbswitch: Found discrete VGA device 0000:0a:00.0: \_SB_.PCI0.RP05.PEGP
[   29.551738] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   29.551806] bbswitch: detected an Optimus _DSM function
[   29.551815] bbswitch: Succesfully loaded. Discrete card 0000:0a:00.0 is on
[   33.104807] vgaarb: this pci device is not a vga device
[   33.129830] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129857] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129869] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129881] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129892] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129903] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129934] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.129947] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.146190] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.651431] vgaarb: this pci device is not a vga device
[   34.491800] init: plymouth-upstart-bridge main process ended, respawning
[   78.354725] show_signal_msg: 105 callbacks suppressed
[   78.354731] xpad[2289]: segfault at 7f01e430b6b8 ip 00007f01e428ac65 sp 00007fffa589c0a0 error 7 in libglib-2.0.so.0.4002.0[7f01e4226000+106000]
[  690.774882] [drm] Module unloaded
[  690.798661] bbswitch: disabling discrete graphics
[  690.798674] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  690.813919] pci 0000:0a:00.0: Refused to change power state, currently in D0
[  788.042375] bbswitch: enabling discrete graphics
[  788.577979] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:0a:00.0 on minor 1
[  788.577992] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.82  Wed Jun 17 10:37:46 PDT 2015
[  788.600910] vgaarb: this pci device is not a vga device
[  788.603217] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603243] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603255] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603265] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603276] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603286] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603316] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.603327] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  788.620135] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  789.027268] vgaarb: this pci device is not a vga device
[ 1396.341702] systemd-hostnamed[6325]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1837.805216] [drm] Module unloaded
[ 1837.821208] bbswitch: disabling discrete graphics
[ 1837.821221] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[ 1837.836219] pci 0000:0a:00.0: Refused to change power state, currently in D0
```

---

### Post by Bashing-om on 2015-09-26
Geosearchef; Uhggg ..

Not the result hoped for. The majority of the errors are ACPI related. Maybe try try a few ACPI boot parameters ?
I no longer have access to a laptop machine to test with, and thus can not directly advise in what parameters might be beneficial in your case.

What machine are we working with ; And what release and DeskTop environment is at play here ?

I really do not know what to make of the Nvidia reported errors:
> 
11.538882] nvidia: module license 'NVIDIA' taints kernel.
[   11.538885] Disabling lock debugging due to kernel taint
[   11.541042] nvidia: module verification failed: signature and/or  required key missing - tainting kernel

Nvidia recommends the 352 driver for that Nvidia card, but I would expect the loaded 346 driver to be good . However, will not hurt to try and install the 352 version.
Is the 352 version offered in our repo or must we obtain the driver from our trusted PPA ?
```

sudo ubuntu-drivers list

```

As another wayward thought, do you have Dynamic Kernel Mode Setting for graphics available ?
```

sudo dkms status
/usr/lib/nux/unity_support_test -p -f

```

[INDENT][INDENT]It is cause and effect
[INDENT][INDENT]matching up the hardware
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Geosearchef on 2015-09-26
Version 352 is not available in default repo.
```
geosearchef@geosearchef-ubuntu:~$ sudo ubuntu-drivers list

nvidia-340-updates
nvidia-346
nvidia-346-updates
nvidia-340
```

```
geosearchef@geosearchef-ubuntu:~$ sudo dkms status
bbswitch, 0.8, 3.19.0-28-generic, x86_64: installed
nvidia-346, 346.82, 3.19.0-28-generic, x86_64: installed
```


Running on dedicated card:
```
geosearchef@geosearchef-ubuntu:~$ /usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 740M/PCIe/SSE2
OpenGL version string:  4.5.0 NVIDIA 346.82

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Laptop is a HP Pavillion 15.
OS: Ubuntu 14.04
Desktop-Environnement: Unity
Kernel-Version: 3.19.0-28-generic
CPU: Intel i7-4500U
GPU: NVIDIA GT 740M
RAM: 8GB

I've also got a second monitor plugged in using a hdmi to vga converter but I disconnect it when testing.

---

### Post by mc4man on 2015-09-26
just a few things - 
there doesn't seem to be anything in the log that's wrong concerning nvidia
(the log seems to be over quite some time, you switched from nvidia to intel & back a few times. Worst thing apparent is xpad crashed.

As far as nvidia thru nvidia-prime - 
nvidia-prime thru gpu-manager creates an xorg.conf for you, you shouldn't create one thru nvidia. (though it can be edited after the fact if need be. Every time you switch from intel to nvidia it creates a new xorg.conf, everytime you switch from nvidia to intel it renames xorg.conf as when on intel it can't be there. The should be a gpu-manager log file in /var/log

I'd expect a laptop using nvidia graphics to be a little hotter, how much could depend on your cooling & environment. Maybe check the nvidia temps in nvidia-settings & also check your cpu temps & frequencies

I'd also make sure any primus packages are gone & ck. autoremove.

(by default any Ubuntu nvidia package 331 or higher installs everything needed for nvidia-prime.

---

