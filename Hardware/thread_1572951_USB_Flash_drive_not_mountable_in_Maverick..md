---
title: "USB Flash drive not mountable in Maverick."
date: 2010-09-12
forum: Hardware
---

### Post by karimruan on 2010-09-12
I just today did a clean install of 10.10 on my HP DV6929wm (walmart special apparently). My CPU is 64bit, but I always run the 32bit version in favor of compatibility and stability (mainly in regards to flash).

In every release since 9.04 (I always upgrade, even if it is not LTS) usb has worked fine, with the minor issue of the drive occasionally thinking it is too full to add files even after a reformat.

My lappy has 4 usb ports, and I tested each port with my only remaining flash drive, a cheap PNY 4GB. Running lsusb each time I reconnected my flash drive, it would not show anything besides my webcam (built into the lappy).

Running lsusb after attaching a gamepad I found laying around shows that Ubuntu is able to use all four USB ports. I have used this drive countless times from 9.04 to 10.04 with minimal aggrevation.

Here is the output of 'lsusb' with the PNY 4GB flash drive as well  as the gamepade connected via usb (it also shows a usb 2.0 camera, which I assume to be my built in webcam, right?):

```

kimo@kimo-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kimo@kimo-laptop:~$ 

```

And, whether this will be helpful or not, the output for 'dmesg' (It's quite long):

```

[   17.334506] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   17.334510] hda_intel: Disable MSI for Nvidia chipset
[   17.334555] HDA Intel 0000:00:07.0: setting latency timer to 64
[   17.357452] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   17.357459]   alloc irq_desc for 19 on node -1
[   17.357462]   alloc kstat_irqs on node -1
[   17.357473] ath5k 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   17.357482] ath5k 0000:03:00.0: setting latency timer to 64
[   17.357530] ath5k 0000:03:00.0: registered as 'phy0'
[   17.860059] ath: EEPROM regdomain: 0x64
[   17.860063] ath: EEPROM indicates we should expect a direct regpair map
[   17.860067] ath: Country alpha2 being used: 00
[   17.860069] ath: Regpair used: 0x64
[   17.929413] phy0: Selected rate control algorithm 'minstrel'
[   17.930067] Registered led device: ath5k-phy0::rx
[   17.930085] Registered led device: ath5k-phy0::tx
[   17.930089] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.045789] type=1400 audit(1284265731.980:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=821 comm="apparmor_parser"
[   18.049368] type=1400 audit(1284265731.984:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=822 comm="apparmor_parser"
[   18.049686] type=1400 audit(1284265731.984:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=822 comm="apparmor_parser"
[   18.049867] type=1400 audit(1284265731.984:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=822 comm="apparmor_parser"
[   18.054101] type=1400 audit(1284265731.988:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=823 comm="apparmor_parser"
[   18.059038] type=1400 audit(1284265731.992:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=823 comm="apparmor_parser"
[   18.063134] type=1400 audit(1284265731.996:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=825 comm="apparmor_parser"
[   18.231643] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000/0x0
[   18.315120] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.317117] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   18.497756]   alloc irq_desc for 42 on node -1
[   18.497760]   alloc kstat_irqs on node -1
[   18.497770] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   18.497971] eth0: no link during initialization.
[   18.498612] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.539410] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   18.539418]   alloc irq_desc for 16 on node -1
[   18.539421]   alloc kstat_irqs on node -1
[   18.539433] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   18.539441] nvidia 0000:00:12.0: setting latency timer to 64
[   18.539446] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.539932] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.53  Fri Aug 27 21:03:42 PDT 2010
[   18.568255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.736349] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.736353] vboxdrv: Successfully done.
[   18.736356] vboxdrv: Found 2 processor cores.
[   18.736985] vboxdrv: fAsync=1 offMin=0x708c72 offMax=0x708c72
[   18.738102] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   18.738106] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   19.027805] ppdev: user-space parallel port driver
[   19.280902] ata3.00: configured for UDMA/100
[   19.280906] ata3: EH complete
[   21.291421] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.222999] ata3.00: configured for UDMA/100
[   23.223006] ata3: EH complete
[   24.728856] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   79.778858] wlan0: authenticate with 00:17:3f:be:bd:4c (try 1)
[   79.781715] wlan0: authenticated
[   79.781744] wlan0: associate with 00:17:3f:be:bd:4c (try 1)
[   79.783817] wlan0: RX AssocResp from 00:17:3f:be:bd:4c (capab=0x411 status=0 aid=1)
[   79.783824] wlan0: associated
[   79.784631] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.004050] Clocksource tsc unstable (delta = -281845446 ns)
[   90.672031] wlan0: no IPv6 routers present
[  299.074007] ata3.00: configured for UDMA/100
[  299.074019] ata3: EH complete
[  299.221216] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  300.596138] wlan0: deauthenticating from 00:17:3f:be:bd:4c by local choice (reason=3)
[  300.649851] cfg80211: All devices are disconnected, going to restore regulatory settings
[  300.649869] cfg80211: Restoring regulatory settings
[  300.649879] cfg80211: Calling CRDA to update world regulatory domain
[  300.660096] cfg80211: World regulatory domain updated:
[  300.660105]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  300.660115]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  300.660124]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  300.660131]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  300.660139]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  300.660147]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  301.401896] PM: Syncing filesystems ... done.
[  301.404022] PM: Preparing system for mem sleep
[  301.404039] Freezing user space processes ... (elapsed 0.02 seconds) done.
[  301.424056] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  301.440042] PM: Entering mem sleep
[  301.440057] Suspending console(s) (use no_console_suspend to debug)
[  301.453213] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[  301.538984] ACPI handle has no context!
[  301.539936] ACPI handle has no context!
[  301.539944] sdhci-pci 0000:02:05.1: PCI INT B disabled
[  301.539948] ACPI handle has no context!
[  301.556714] forcedeth 0000:00:0a.0: PCI INT A disabled
[  301.556755] ehci_hcd 0000:00:04.1: PCI INT B disabled
[  301.556764] ohci_hcd 0000:00:04.0: PCI INT A disabled
[  301.556778] ehci_hcd 0000:00:02.1: PCI INT B disabled
[  301.556786] ohci_hcd 0000:00:02.0: PCI INT A disabled
[  301.556857] ata2: port disabled. ignoring.
[  301.599142] sd 2:0:0:0: [sda] Stopping disk
[  301.740027] HDA Intel 0000:00:07.0: PCI INT A disabled
[  301.756016] PM: suspend of drv:HDA Intel dev:0000:00:07.0 complete after 199.281 msecs
[  302.093725] PM: suspend of drv:sd dev:2:0:0:0 complete after 640.517 msecs
[  302.093733] PM: suspend of drv:scsi dev:target2:0:0 complete after 640.476 msecs
[  302.093740] PM: suspend of drv:scsi dev:host2 complete after 640.434 msecs
[  302.160070] ahci 0000:00:09.0: PCI INT A disabled
[  302.176016] PM: suspend of drv:ahci dev:0000:00:09.0 complete after 619.289 msecs
[  302.738148] PM: suspend of drv:nvidia dev:0000:00:12.0 complete after 1199.054 msecs
[  302.738168] PM: suspend of drv: dev:pci0000:00 complete after 1181.361 msecs
[  302.738176] PM: suspend of devices complete after 1297.882 msecs
[  302.738179] PM: suspend devices took 1.300 seconds
[  302.816249] PM: late suspend of devices complete after 78.065 msecs
[  302.816334] ACPI: Preparing to enter system sleep state S3
[  302.816478] PM: Saving platform NVS memory
[  302.816595] Disabling non-boot CPUs ...
[  302.920024] CPU 1 is now offline
[  302.920026] SMP alternatives: switching to UP code
[  302.924439] Extended CMOS year: 2000
[  302.924439] Back to C!
[  302.924439] PM: Restoring platform NVS memory
[  302.924439] Extended CMOS year: 2000
[  302.933369] Enabling non-boot CPUs ...
[  302.933568] SMP alternatives: switching to SMP code
[  302.937396] Booting Node 0 Processor 1 APIC 0x1
[  302.923960] Initializing CPU#1
[  303.028215] Switch to broadcast mode on CPU1
[  303.044322] CPU1 is up
[  303.044477] ACPI: Waking up from system sleep state S3
[  303.045267] pci 0000:00:01.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020b)
[  303.045319] ohci_hcd 0000:00:02.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[  303.045344] ehci_hcd 0000:00:02.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[  303.045370] ohci_hcd 0000:00:04.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[  303.045394] ehci_hcd 0000:00:04.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[  303.045433] HDA Intel 0000:00:07.0: restoring config space at offset 0xf (was 0x5020100, writing 0x502010a)
[  303.045442] HDA Intel 0000:00:07.0: restoring config space at offset 0x4 (was 0x0, writing 0xf6480000)
[  303.045448] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[  303.045505] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045573] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045648] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045732] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045749] pcieport 0000:00:0c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[  303.045826] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045840] pcieport 0000:00:0d.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[  303.045846] pcieport 0000:00:0d.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[  303.045927] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  303.045990] firewire_ohci 0000:02:05.0: restoring config space at offset 0x4 (was 0x0, writing 0xf6100000)
[  303.045997] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100100, writing 0x2100106)
[  303.046008] firewire_ohci 0000:02:05.0: proprietary Ricoh MMC controller disabled (via firewire function)
[  303.046011] firewire_ohci 0000:02:05.0: MMC cards are now supported by standard SDHCI controller
[  303.046021] sdhci-pci 0000:02:05.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[  303.046034] sdhci-pci 0000:02:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xf6100800)
[  303.046039] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[  303.046044] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  303.046059] pci 0000:02:05.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[  303.046072] pci 0000:02:05.2: restoring config space at offset 0x4 (was 0x0, writing 0xf6101000)
[  303.046076] pci 0000:02:05.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[  303.046082] pci 0000:02:05.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  303.046097] r852 0000:02:05.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[  303.046109] r852 0000:02:05.3: restoring config space at offset 0x4 (was 0x0, writing 0xf6101400)
[  303.046114] r852 0000:02:05.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[  303.046119] r852 0000:02:05.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  303.046144] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  303.046158] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6000004)
[  303.046163] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  303.046169] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  303.046537] PM: early resume of devices complete after 1.522 msecs
[  303.046654] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[  303.046661] ohci_hcd 0000:00:02.0: setting latency timer to 64
[  303.046676] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[  303.046680] ehci_hcd 0000:00:02.1: setting latency timer to 64
[  303.046698] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[  303.046701] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[  303.046706] ohci_hcd 0000:00:04.0: setting latency timer to 64
[  303.046708] ehci_hcd 0000:00:04.1: setting latency timer to 64
[  303.046724] pata_amd 0000:00:06.0: setting latency timer to 64
[  303.046750] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[  303.046755] HDA Intel 0000:00:07.0: setting latency timer to 64
[  303.046788] pci 0000:00:08.0: setting latency timer to 64
[  303.046799] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[  303.046802] ahci 0000:00:09.0: setting latency timer to 64
[  303.047495] ata2: port disabled. ignoring.
[  303.047656] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[  303.047683] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[  303.049301] sd 2:0:0:0: [sda] Starting disk
[  303.176566] firewire_core: skipped bus generations, destroying all nodes
[  303.184022] PM: resume of drv:firewire_ohci dev:0000:02:05.0 complete after 136.389 msecs
[  303.320299] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[  303.320303] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  303.320333] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[  303.336246] ata1.00: configured for MWDMA2
[  303.364022] ata5: SATA link down (SStatus 0 SControl 300)
[  303.364039] ata6: SATA link down (SStatus 0 SControl 300)
[  303.364050] ata4: SATA link down (SStatus 0 SControl 300)
[  303.568460] PM: resume of drv:forcedeth dev:0000:00:0a.0 complete after 521.629 msecs
[  303.568469] PM: resume of drv:net dev:eth0 complete after 414.064 msecs
[  303.868948] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  303.874942] ata3.00: configured for UDMA/100
[  303.895570] PM: resume of drv:sd dev:2:0:0:0 complete after 846.271 msecs
[  303.895592] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 845.940 msecs
[  303.895598] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 327.110 msecs
[  304.792851] firewire_core: rediscovered device fw0
[  304.796267] PM: resume of drv:nvidia dev:0000:00:12.0 complete after 1748.793 msecs
[  304.796286] PM: resume of drv:i2c dev:i2c-2 complete after 898.433 msecs
[  304.796307] PM: resume of devices complete after 1749.721 msecs
[  304.796513] PM: resume devices took 1.752 seconds
[  304.796547] PM: Finishing wakeup.
[  304.796549] Restarting tasks ... done.
[  304.797056] video LNXVIDEO:00: Restoring backlight state
[  304.987871] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[  304.988011] eth0: no link during initialization.
[  304.988726] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  306.451352] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  307.217079] ata3.00: configured for UDMA/100
[  307.217084] ata3: EH complete
[  307.655934] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  308.043255] wlan0: authenticate with 00:17:3f:be:bd:4c (try 1)
[  308.044800] wlan0: authenticated
[  308.044881] wlan0: associate with 00:17:3f:be:bd:4c (try 1)
[  308.047211] wlan0: RX AssocResp from 00:17:3f:be:bd:4c (capab=0x411 status=0 aid=1)
[  308.047221] wlan0: associated
[  308.049237] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  319.048040] wlan0: no IPv6 routers present
[ 1060.685851] ata3.00: configured for UDMA/100
[ 1060.685863] ata3: EH complete
[ 1060.886533] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1061.793136] wlan0: deauthenticating from 00:17:3f:be:bd:4c by local choice (reason=3)
[ 1061.841903] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1061.841923] cfg80211: Restoring regulatory settings
[ 1061.841933] cfg80211: Calling CRDA to update world regulatory domain
[ 1061.852308] cfg80211: World regulatory domain updated:
[ 1061.852319]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1061.852328]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1061.852336]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1061.852344]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1061.852352]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1061.852359]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1062.488645] PM: Syncing filesystems ... done.
[ 1062.491008] PM: Preparing system for mem sleep
[ 1062.491023] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 1062.505055] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 1062.521043] PM: Entering mem sleep
[ 1062.521058] Suspending console(s) (use no_console_suspend to debug)
[ 1062.540209] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 1062.625655] ACPI handle has no context!
[ 1062.626609] ACPI handle has no context!
[ 1062.626617] sdhci-pci 0000:02:05.1: PCI INT B disabled
[ 1062.626621] ACPI handle has no context!
[ 1062.641738] ehci_hcd 0000:00:04.1: PCI INT B disabled
[ 1062.641748] ohci_hcd 0000:00:04.0: PCI INT A disabled
[ 1062.641761] ehci_hcd 0000:00:02.1: PCI INT B disabled
[ 1062.641769] ohci_hcd 0000:00:02.0: PCI INT A disabled
[ 1062.641843] ata2: port disabled. ignoring.
[ 1062.648674] sd 2:0:0:0: [sda] Stopping disk
[ 1062.769031] HDA Intel 0000:00:07.0: PCI INT A disabled
[ 1062.785017] PM: suspend of drv:HDA Intel dev:0000:00:07.0 complete after 143.299 msecs
[ 1063.143910] PM: suspend of drv:sd dev:2:0:0:0 complete after 603.706 msecs
[ 1063.143918] PM: suspend of drv:scsi dev:target2:0:0 complete after 603.625 msecs
[ 1063.143924] PM: suspend of drv:scsi dev:host2 complete after 603.582 msecs
[ 1063.205072] ahci 0000:00:09.0: PCI INT A disabled
[ 1063.221018] PM: suspend of drv:ahci dev:0000:00:09.0 complete after 579.308 msecs
[ 1063.822419] PM: suspend of drv:nvidia dev:0000:00:12.0 complete after 1196.656 msecs
[ 1063.822438] PM: suspend of drv: dev:pci0000:00 complete after 1180.648 msecs
[ 1063.822447] PM: suspend of devices complete after 1301.147 msecs
[ 1063.822451] PM: suspend devices took 1.300 seconds
[ 1063.900245] PM: late suspend of devices complete after 77.790 msecs
[ 1063.900344] ACPI: Preparing to enter system sleep state S3
[ 1063.900491] PM: Saving platform NVS memory
[ 1063.900611] Disabling non-boot CPUs ...
[ 1064.004019] CPU 1 is now offline
[ 1064.004022] SMP alternatives: switching to UP code
[ 1064.008374] Extended CMOS year: 2000
[ 1064.008374] Back to C!
[ 1064.008374] PM: Restoring platform NVS memory
[ 1064.008374] Extended CMOS year: 2000
[ 1064.017304] Enabling non-boot CPUs ...
[ 1064.017502] SMP alternatives: switching to SMP code
[ 1064.021320] Booting Node 0 Processor 1 APIC 0x1
[ 1064.007928] Initializing CPU#1
[ 1064.112194] Switch to broadcast mode on CPU1
[ 1064.128327] CPU1 is up
[ 1064.128482] ACPI: Waking up from system sleep state S3
[ 1064.129274] pci 0000:00:01.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020b)
[ 1064.129326] ohci_hcd 0000:00:02.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 1064.129352] ehci_hcd 0000:00:02.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 1064.129377] ohci_hcd 0000:00:04.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 1064.129401] ehci_hcd 0000:00:04.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 1064.129440] HDA Intel 0000:00:07.0: restoring config space at offset 0xf (was 0x5020100, writing 0x502010a)
[ 1064.129449] HDA Intel 0000:00:07.0: restoring config space at offset 0x4 (was 0x0, writing 0xf6480000)
[ 1064.129454] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00002)
[ 1064.129512] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129581] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129655] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129738] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129755] pcieport 0000:00:0c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 1064.129832] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129848] pcieport 0000:00:0d.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 1064.129929] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 1064.129993] firewire_ohci 0000:02:05.0: restoring config space at offset 0x4 (was 0x0, writing 0xf6100000)
[ 1064.129999] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100100, writing 0x2100106)
[ 1064.130011] firewire_ohci 0000:02:05.0: proprietary Ricoh MMC controller disabled (via firewire function)
[ 1064.130013] firewire_ohci 0000:02:05.0: MMC cards are now supported by standard SDHCI controller
[ 1064.130024] sdhci-pci 0000:02:05.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 1064.130037] sdhci-pci 0000:02:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xf6100800)
[ 1064.130041] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 1064.130047] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 1064.130062] pci 0000:02:05.2: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 1064.130074] pci 0000:02:05.2: restoring config space at offset 0x4 (was 0x0, writing 0xf6101000)
[ 1064.130079] pci 0000:02:05.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 1064.130084] pci 0000:02:05.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 1064.130099] r852 0000:02:05.3: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 1064.130112] r852 0000:02:05.3: restoring config space at offset 0x4 (was 0x0, writing 0xf6101400)
[ 1064.130117] r852 0000:02:05.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 1064.130122] r852 0000:02:05.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 1064.130146] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1064.130161] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6000004)
[ 1064.130165] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1064.130171] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1064.130541] PM: early resume of devices complete after 1.518 msecs
[ 1064.130658] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[ 1064.130664] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 1064.130681] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[ 1064.130686] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 1064.130704] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[ 1064.130709] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[ 1064.130714] ohci_hcd 0000:00:04.0: setting latency timer to 64
[ 1064.130717] ehci_hcd 0000:00:04.1: setting latency timer to 64
[ 1064.130730] pata_amd 0000:00:06.0: setting latency timer to 64
[ 1064.130752] pci 0000:00:08.0: setting latency timer to 64
[ 1064.130763] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[ 1064.130766] ahci 0000:00:09.0: setting latency timer to 64
[ 1064.131578] ata2: port disabled. ignoring.
[ 1064.131629] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[ 1064.131633] HDA Intel 0000:00:07.0: setting latency timer to 64
[ 1064.132222] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[ 1064.132225] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 1064.134304] sd 2:0:0:0: [sda] Starting disk
[ 1064.261111] firewire_core: skipped bus generations, destroying all nodes
[ 1064.269021] PM: resume of drv:firewire_ohci dev:0000:02:05.0 complete after 137.343 msecs
[ 1064.405297] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 1064.405301] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 1064.405332] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[ 1064.421245] ata1.00: configured for MWDMA2
[ 1064.449024] ata6: SATA link down (SStatus 0 SControl 300)
[ 1064.449038] ata5: SATA link down (SStatus 0 SControl 300)
[ 1064.449049] ata4: SATA link down (SStatus 0 SControl 300)
[ 1064.649492] PM: resume of drv:forcedeth dev:0000:00:0a.0 complete after 518.696 msecs
[ 1064.649501] PM: resume of drv:net dev:eth0 complete after 409.888 msecs
[ 1064.761953] firewire_core: rediscovered device fw0
[ 1064.953022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1064.964942] ata3.00: configured for UDMA/100
[ 1064.985566] PM: resume of drv:sd dev:2:0:0:0 complete after 851.263 msecs
[ 1064.985575] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 851.231 msecs
[ 1064.985581] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 336.060 msecs
[ 1065.878182] PM: resume of drv:nvidia dev:0000:00:12.0 complete after 1746.630 msecs
[ 1065.879241] PM: resume of drv:i2c dev:i2c-2 complete after 891.407 msecs
[ 1065.879263] PM: resume of devices complete after 1748.671 msecs
[ 1065.879464] PM: resume devices took 1.748 seconds
[ 1065.879496] PM: Finishing wakeup.
[ 1065.879498] Restarting tasks ... done.
[ 1065.879917] video LNXVIDEO:00: Restoring backlight state
[ 1065.976032] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[ 1065.976241] eth0: no link during initialization.
[ 1065.976894] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1066.036528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1068.167761] ata3.00: configured for UDMA/100
[ 1068.167770] ata3: EH complete
[ 1068.599446] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1069.119639] wlan0: authenticate with 00:17:3f:be:bd:4c (try 1)
[ 1069.121470] wlan0: authenticated
[ 1069.121521] wlan0: associate with 00:17:3f:be:bd:4c (try 1)
[ 1069.123632] wlan0: RX AssocResp from 00:17:3f:be:bd:4c (capab=0x411 status=0 aid=1)
[ 1069.123641] wlan0: associated
[ 1069.125243] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1077.480071] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1080.112035] wlan0: no IPv6 routers present
[ 1379.840074] usb 3-1: new low speed USB device using ohci_hcd and address 2
[ 1380.139407] usbcore: registered new interface driver hiddev
[ 1380.139613] usbcore: registered new interface driver usbhid
[ 1380.139619] usbhid: USB HID core driver
[ 1380.174091] input: DragonRise Inc.   Generic   USB  Joystick   as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input10
[ 1380.174458] dragonrise 0003:0079:0006.0001: input,hidraw0: USB HID v1.10 Joystick [DragonRise Inc.   Generic   USB  Joystick  ] on usb-0000:00:02.0-1/input0
[ 1380.174489] dragonrise 0003:0079:0006.0001: Force Feedback for DragonRise Inc. game controllers by Richard Walmsley <richwalm@gmail.com>
kimo@kimo-laptop:~$ 

```


I decided to  test the prelease versions just because I have used and loved Ubuntu for over a year now, and want to do whatever I can to help improve it. Any suggestions on how I can help improve ubuntu just by using it would be great, lord knows I love my Ubuntu!

Thanks ahead for anyhelp I recieve, it is much appreciated!

---

### Post by wilee-nilee on 2010-09-12
Have you looked to see if gparted sees the thumb, and if so if there are any errors, or if it sees it, can you reformat it? It sounds like a problem from the thumb, I have Maverick running, full USB access. Have you tried this thumb on other computers as well in this process?

---

### Post by karimruan on 2010-09-12
> **wilee-nilee said:**
> Have you looked to see if gparted sees the thumb, and if so if there are any errors, or if it sees it, can you reformat it? It sounds like a problem from the thumb, I have Maverick running, full USB access. Have you tried this thumb on other computers as well in this process?

Thanks for the reply, I will check gparted, didn't even think of that. 
I have used this thumb since 9.04 on this computer, and just recently used it to backup files from my mother-in-law's dell lappy before I reformatted it. After the reformat/install, the drive was fine getting them back onto her HDD.

Then, I used the same drive (did not reformat, it still has some pretty important docs  I need, so it is still fat(16 or  32, can't remember) on a friends Mac because he wanted some app and did not have net access. It was fine after that. 

Brought it home, stuck it in our new desktop that ran Vista Ultimate, backed up whatever my wife had added to it, and installed 10.04. Works fine there. Works fine everywhere, even on my lappy if I install 9.04 - 10.04. Just seems like 10.10 doesn't like my drive.

I'll post back with info on my gparted experience, thanks!

---

### Post by karimruan on 2010-09-12
OK, gparted shows only my  HDD, /dev/sda1, sda2, and sda5 (sda5 is my swap apparently).

At first, I also had an SD card connected to my internal card reader. Gparted only showed the SD card and no HDD. I removed the SD card and refreshed gparted, and there, my HDD shows, but no thumb drive, in any ofthe four ports.

Works in every other computer, even on this one with Windows or Ubuntu (9.04-9.10). I have until monday to play with this the way it is, then I will need to install windows for work :(

Thank god for vbox! But, to do that in 10.10, I will need USB support. It just seems to be being picky about thumbs. My USB MP3 player works fine, and it is 2gb. 


CORRECTION: If I said my Thumb is a PNY 2 GB, I mean PNY 4GB. Sorry for any misunderstanding that may have caused, if I did mess up. I'll find out once I post this, lol.

Thanks again, I appreciate it!

---

### Post by wilee-nilee on 2010-09-12
Just for kicks I would boot the computer without anything external plugged in but the thumb, power, and ethernet, and see if maybe the other stuff being plugged in may be the problem.

Otherwise this is a strange anomaly, maybe if you reformat the thumb in windows it will work who knows?

---

### Post by karimruan on 2010-09-12
I already thought of that. I tried many different combinations, kind of makes me feel a little nutty..lol.

Tried with only USB Thumb connected, without my cooling pad, no gamepad, no SD card, with ethernet and wireless only, nothing in dvd drive, video disk in dvd drive, live cd in dvd drive (turns out I was a little tired and was wondering how the XP install had come up, lol).

I am really hoping to avoid having to reformat. I know I can just install 9.04 and it will read my thumb fine (I just tried that last night, and then reinstalled maverick again).  What I should have done is backed up my thumb drive to my SD card or something, because I really can't lose my documents on their, my boss would kill me. Plus, I have alot of movies, music, the occassional pdf and a crap load of windows XP/VISTA/7 drivers for dell, HP, Toshiba, and Asus lappies, all neatly organized in folders labeled after their respective models, and I even put a text file in each folder with each lappies specs, certain install/post install notes... I spent a lot of time on this drive.Yet, through my own stubborness, I just can't make myself reinstall 9.04 to back up the drive....

lsusb shows nothing, I did not understand much of dmesg, disk utility doesn't show the thumb, nor does gparted. Is this a bug (seeing as the thumb works everywhere else) or am I missing some super simple concept here? Wouldn't be the first time. One time after a clean install I forgot to actually connect to my wireless network (wifi has worked out of the box since 9.04, no luck in 8.10 :) and installed the madwifi driver, thus for some reason breaking wifi altogether.

OK, enough irrelevant info. I tried rebooting with various combos of attached devices, even without attached devices. Complete no-go.

---

### Post by karimruan on 2010-11-10
Kind of forgot about this thread, sorry mods.

Tried the thumb drive on several other computers between family and friends, mostly windows computers, none would see the drive. I chalked it up as a loss once I saw what looked like my sons teeth prints.

Sorry for neglecting to post the outcome.

---

