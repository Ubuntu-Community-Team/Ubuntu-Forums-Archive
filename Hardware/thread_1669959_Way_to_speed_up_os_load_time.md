---
title: "Way to speed up o/s load time ?"
date: 2011-01-18
forum: Hardware
---

### Post by smurphy_it on 2011-01-18
Good day folks.  Any idea how to speed up the o/s load time.  Grub menu doesn't display by default and is set at zero.  It does load quite/splash though.

When looking in dmesg I see the following:

NXVIDEO:00/input/input7
[    2.353300] ACPI: Video Device [C099] (multi-head: yes  rom: no  post: no)
[    2.353359] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.356162] vga16fb: initializing
[    2.356167] vga16fb: mapped to 0xc00a0000
[    2.356173] vga16fb: not registering due to another framebuffer present
[    2.514131] Console: switching to colour frame buffer device 160x50
[    2.661318] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b249929e10310]
[   10.717076] CE: hpet increasing min_delta_ns to 15000 nsec
[   11.392079] CE: hpet increasing min_delta_ns to 22500 nsec
[B][   15.182787] EXT4-fs (dm-1): mounted filesystem with ordered data mode
[   42.797687] udev: starting version 151[/B]
[   42.951268] lp: driver loaded but no devices found
[   43.076808] lis3lv02d: hardware type NC2510 found.
[   43.145800] lis3lv02d: 2-byte sensor found
[   43.321400] type=1505 audit(1295373124.069:2):  operation="profile_load" pid=736 name="/sbin/dhclient3"
[   43.322675] type=1505 audit(1295373124.069:3):  operation="profile_load" pid=736 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   43.323407] type=1505 audit(1295373124.069:4):  operation="profile_load" pid=736 name="/usr/lib/connman/scripts/dhclient-script"
[   43.335397] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   43.336652] Registered led device: hp::hddprotect
[   43.336758] lis3lv02d driver loaded.
[   43.342565] cfg80211: Calling CRDA to update world regulatory domain
[   43.358302] sdhci: Secure Digital Host Controller Interface driver
[   43.358306] sdhci: Copyright(c) Pierre Ossman
[   43.360815] sdhci-pci 0000:02:06.2: SDHCI controller found [1180:0822] (rev 21)
[   43.360859] sdhci-pci 0000:02:06.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[   43.362961] Registered led device: mmc0::
[   43.379099] mmc0: SDHCI controller on PCI [0000:02:06.2] using PIO
[   43.380441] ricoh-mmc: Ricoh MMC Controller disabling driver
[   43.380445] ricoh-mmc: Copyright(c) Philip Langdale
[   43.380484] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.3 [1180:0843] (rev 11)
[   43.380531] ricoh-mmc: Controller is now disabled.
[   43.401568] cfg80211: World regulatory domain updated:
[   43.401574] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   43.401579] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.401584] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   43.401588] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   43.401592] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.401597] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.451891] tpm_tis 00:02: 1.2 TPM (device-id 0xB, rev-id 16)
[   43.494370] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:30c9]
[   43.520155] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   43.520160] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   43.520291] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   43.520330] iwlagn 0000:10:00.0: setting latency timer to 64
[   43.520438] iwlagn 0000:10:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   43.621841] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0cb8, PCI irq 18
[   43.621849] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   43.621856] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   43.621870] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   43.621876] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   43.622276] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe03fffff
[   43.622281] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   43.622756] iwlagn 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   43.623070]   alloc irq_desc for 28 on node -1
[   43.623074]   alloc kstat_irqs on node -1
[   43.623101] iwlagn 0000:10:00.0: irq 28 for MSI/MSI-X
[   43.632042] RPC: Registered udp transport module.
[   43.632047] RPC: Registered tcp transport module.
[   43.632051] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   43.644017] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   43.675841] psmouse serio1: ID: 10 00 64
[   43.785230] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   43.785303] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   43.785323] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   43.785371] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   43.891026] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   44.086641] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   44.088940] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   44.089941] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   44.090769] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   44.091857] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   44.197890] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input10
[   44.775740] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   44.806990] type=1505 audit(1295373125.553:5):  operation="profile_replace" pid=1090 name="/sbin/dhclient3"
[   44.808384] type=1505 audit(1295373125.557:6):  operation="profile_replace" pid=1090 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   44.809132] type=1505 audit(1295373125.557:7):  operation="profile_replace" pid=1090 name="/usr/lib/connman/scripts/dhclient-script"
[   44.819105] type=1505 audit(1295373125.565:8):  operation="profile_load" pid=1093 name="/usr/lib/cups/backend/cups-pdf"
[   44.822151] type=1505 audit(1295373125.569:9):  operation="profile_load" pid=1093 name="/usr/sbin/cupsd"
[   44.823173] type=1505 audit(1295373125.569:10):  operation="profile_load" pid=1091 name="/usr/bin/evince"
[   44.828467] type=1505 audit(1295373125.577:11):  operation="profile_load" pid=1094 name="/usr/sbin/tcpdump"
[   44.856941] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   44.896238] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   45.225532] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[   45.281132] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[   45.281555] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.007836] svc: failed to register lockdv1 RPC service (errno 97).
[   46.009502] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   46.040331] NFSD: starting 90-second grace period
[   46.309846] ppdev: user-space parallel port driver
[   46.677639] Adding 3219448k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:3219448k 
[   46.681932] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   46.681939] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   46.682306] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   50.325292] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   57.432050] eth0: no IPv6 routers present


What's concerning is why such a time differential from 15 seconds to 42 seconds. Bolded above.  Any suggestions ?  Need any further info ?

PS.  Laptop = HP compaq 2510p

---

