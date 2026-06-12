---
title: "uvc video camera is suddenly not being detected"
date: 2009-11-22
forum: Hardware
---

### Post by sexyclient2 on 2009-11-22
My video camera was one fo those things that always worked, and I was proud.  One day, though, my camera just stopped being detected whenever I go to "cheese" and I've got no idea why it happened, or how to fix it :(.

I turned on usbcore.autosuspend=1 , but that was a while ago and I'm quite sure that my camera's worked since then, so I can't think of any reason why things just up-and-broke.

Sorry I didn't post my hardware specs, or any log files -- I don't know what and where they are (respectively!)  Can anyone help me?  If so, please do!

---

### Post by sexyclient2 on 2009-11-24
I tried removing usbcore.autosuspend=1 but that failed, now I've no idea where I should start looking...

---

### Post by ubunxpm on 2009-11-24
Run lsusb
Cheese itself is the culprit if your webcam is already in the list. If your device is not in the list try another usb port.

Good luck

---

### Post by sexyclient2 on 2009-11-24
It's an internal camera inside the laptop's lid, so I can't change the port -- but it's listed!  Thanks, I guess cheese is just busted.

---

### Post by PatrickVogeli on 2009-11-24
can you attach the result of dmesg?

---

### Post by sexyclient2 on 2009-11-24
> **PatrickVogeli said:**
> can you attach the result of dmesg?

```

67 name=/usr/bin/evince-previewer
[    4.982491] type=1505 audit(1259021045.559:8): operation="profile_load" pid=467 name=/usr/bin/evince-thumbnailer
[    5.040446] type=1505 audit(1259021045.619:9): operation="profile_load" pid=469 name=/usr/lib/cups/backend/cups-pdf
[    6.590405] usb-storage: device scan complete
[    6.591965] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852S  1.31 PQ: 0 ANSI: 0
[    6.598429] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.598437] Uniform CD-ROM driver Revision: 3.20
[    6.598617] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    6.598721] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    6.850733] Adding 995988k swap on /dev/sda7.  Priority:-1 extents:1 across:995988k 
[    7.727967] EXT4-fs (sda6): internal journal on sda6:8
[    7.773825] usb-storage: device scan complete
[    7.776780] scsi 3:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 4 CCS
[    7.777433] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    7.786769] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    8.306860] udev: starting version 147
[    9.662748] tpm_inf_pnp 00:09: Found TPM with ID IFX0102
[   10.329522] Linux video capture interface: v2.00
[   10.808907] sony-laptop: Sony Programmable IO Control Driver v0.6.
[   10.808934] sony-laptop: detected Type3 model
[   10.813149] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2e/SNY6001:00/input/input5
[   10.813284] input: Sony Vaio Jogdial as /devices/virtual/input/input6
[   10.813409] sony-laptop: device allocated minor is 55
[   10.821658] sony-laptop: Sony Notebook Control Driver v0.6.
[   10.821669] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   10.875685] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   10.892256] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   11.067420] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   11.067617] usbcore: registered new interface driver btusb
[   11.070497] intel_rng: FWH not detected
[   11.568945] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[   11.572165] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   11.572420] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   11.572428] uvcvideo: Failed to initialize the device (-5).
[   11.572522] usbcore: registered new interface driver uvcvideo
[   11.572528] USB Video Class driver (v0.1.0)
[   12.840163] cfg80211: Calling CRDA to update world regulatory domain
[   12.916280] lp: driver loaded but no devices found
[   13.171637] yenta_cardbus 0000:09:04.0: CardBus bridge found [104d:900e]
[   13.320786] yenta_cardbus 0000:09:04.0: ISA IRQ mask 0x0cb8, PCI irq 20
[   13.320794] yenta_cardbus 0000:09:04.0: Socket status: 30000006
[   13.320802] pci_bus 0000:09: Raising subordinate bus# of parent bus (#09) from #0a to #0d
[   13.320816] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   13.320823] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge Memory window: 0xfc100000 - 0xfc1fffff
[   13.320828] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   14.148639] cfg80211: World regulatory domain updated:
[   14.148647]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.148653]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.148658]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.148663]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.148668]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.148672]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.960317] usb 1-6.1: new full speed USB device using ehci_hcd and address 8
[   15.071840] usb 1-6.1: configuration #1 chosen from 1 choice
[   15.459488] usbcore: registered new interface driver usbserial
[   15.459569] USB Serial support registered for generic
[   15.459744] usbcore: registered new interface driver usbserial_generic
[   15.459749] usbserial: USB Serial Driver core
[   15.628915] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.628921] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.629412] iwlagn 0000:03:00.0: power state changed by ACPI to D0
[   15.629437] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.629453] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.629503] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   15.679078] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.679181]   alloc irq_desc for 29 on node 0
[   15.679185]   alloc kstat_irqs on node 0
[   15.679219] iwlagn 0000:03:00.0: irq 29 for MSI/MSI-X
[   15.860498] USB Serial support registered for GSM modem (1-port)
[   15.860615] option 1-6.1:1.0: GSM modem (1-port) converter detected
[   15.860790] usb 1-6.1: GSM modem (1-port) converter now attached to ttyUSB0
[   15.860817] option 1-6.1:1.1: GSM modem (1-port) converter detected
[   15.860911] usb 1-6.1: GSM modem (1-port) converter now attached to ttyUSB1
[   15.860936] option 1-6.1:1.2: GSM modem (1-port) converter detected
[   15.861025] usb 1-6.1: GSM modem (1-port) converter now attached to ttyUSB2
[   15.861051] option 1-6.1:1.3: GSM modem (1-port) converter detected
[   15.861143] usb 1-6.1: GSM modem (1-port) converter now attached to ttyUSB3
[   15.861169] usbcore: registered new interface driver option
[   15.861173] option: v0.7.2:USB Driver for GSM modems
[   16.393381] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.298325] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.298416] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.613882] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   21.877228] sky2 eth0: enabling interface
[   21.877685] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.435511] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.442301] __ratelimit: 9 callbacks suppressed
[   23.442307] type=1505 audit(1259039064.019:13): operation="profile_replace" pid=1132 name=/usr/share/gdm/guest-session/Xsession
[   23.445506] type=1505 audit(1259039064.019:14): operation="profile_replace" pid=1133 name=/sbin/dhclient3
[   23.446836] type=1505 audit(1259039064.019:15): operation="profile_replace" pid=1133 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   23.447574] type=1505 audit(1259039064.019:16): operation="profile_replace" pid=1133 name=/usr/lib/connman/scripts/dhclient-script
[   23.454282] type=1505 audit(1259039064.029:17): operation="profile_replace" pid=1134 name=/usr/bin/evince
[   23.476489] type=1505 audit(1259039064.049:18): operation="profile_replace" pid=1134 name=/usr/bin/evince-previewer
[   23.489328] type=1505 audit(1259039064.059:19): operation="profile_replace" pid=1134 name=/usr/bin/evince-thumbnailer
[   23.507254] type=1505 audit(1259039064.079:20): operation="profile_replace" pid=1136 name=/usr/lib/cups/backend/cups-pdf
[   23.508811] type=1505 audit(1259039064.079:21): operation="profile_replace" pid=1136 name=/usr/sbin/cupsd
[   23.513431] type=1505 audit(1259039064.089:22): operation="profile_replace" pid=1137 name=/usr/sbin/ntpd
[   23.910859] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   24.891989] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   25.105874] Registered led device: iwl-phy0::radio
[   25.105909] Registered led device: iwl-phy0::assoc
[   25.105939] Registered led device: iwl-phy0::RX
[   25.105974] Registered led device: iwl-phy0::TX
[   25.179588] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.610056] i2c-adapter i2c-1: unable to read EDID block.
[   33.610063] i915 0000:00:02.0: LVDS-1: no EDID data
[   33.950180] i2c-adapter i2c-1: unable to read EDID block.
[   33.950190] i915 0000:00:02.0: LVDS-1: no EDID data
[   36.124889] ppdev: user-space parallel port driver
[   36.160869] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.160875] Bluetooth: BNEP filters: protocol multicast
[   36.822892] Bridge firewalling registered
[   48.721276] CE: hpet increasing min_delta_ns to 15000 nsec
[   48.992564] i2c-adapter i2c-1: unable to read EDID block.
[   48.992575] i915 0000:00:02.0: LVDS-1: no EDID data
[   49.232558] i2c-adapter i2c-1: unable to read EDID block.
[   49.232569] i915 0000:00:02.0: LVDS-1: no EDID data
[   49.522557] i2c-adapter i2c-1: unable to read EDID block.
[   49.522567] i915 0000:00:02.0: LVDS-1: no EDID data
[   74.902554] i2c-adapter i2c-1: unable to read EDID block.
[   74.902563] i915 0000:00:02.0: LVDS-1: no EDID data
[   75.110058] i2c-adapter i2c-1: unable to read EDID block.
[   75.110070] i915 0000:00:02.0: LVDS-1: no EDID data
[   75.312568] i2c-adapter i2c-1: unable to read EDID block.
[   75.312579] i915 0000:00:02.0: LVDS-1: no EDID data
[   78.092555] i2c-adapter i2c-1: unable to read EDID block.
[   78.092565] i915 0000:00:02.0: LVDS-1: no EDID data
[   86.014364] wlan0: authenticate with AP 00:1f:90:b3:3c:ac
[   86.016181] wlan0: authenticated
[   86.016185] wlan0: associate with AP 00:1f:90:b3:3c:ac
[   86.018561] wlan0: RX AssocResp from 00:1f:90:b3:3c:ac (capab=0x431 status=0 aid=2)
[   86.018567] wlan0: associated
[   86.038647] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.102130] cfg80211: Calling CRDA for country: US
[   86.105415] cfg80211: Received country IE:
[   86.105421] cfg80211: Regulatory domain: US
[   86.105425]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   86.105430]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   86.105434] cfg80211: CRDA thinks this should applied:
[   86.105437] cfg80211: Regulatory domain: US
[   86.105440]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   86.105445]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   86.105450]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   86.105454]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   86.105459]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   86.105464]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   86.105467] cfg80211: We intersect both of these and get:
[   86.105471] cfg80211: Regulatory domain: 98
[   86.105473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   86.105478]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   86.105487] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   86.105491] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   86.105496] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   86.105500] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   86.105505] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   86.105509] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   86.105514] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   86.105518] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   86.105523] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   86.105527] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   86.105532] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   86.105536] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   86.105540] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   86.105547] cfg80211: Current regulatory domain updated by AP to: US
[   86.105550]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   86.105555]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   96.220041] wlan0: no IPv6 routers present
[ 1531.862577] CE: hpet increasing min_delta_ns to 22500 nsec
[ 3208.142662] sky2 eth0: disabling interface
[ 3208.172845] wlan0: deauthenticating by local choice (reason=3)
[ 3208.328271] wlan0: disassociating by local choice (reason=3)
[ 3210.486475] PM: Syncing filesystems ... done.
[ 3210.608722] PM: Preparing system for mem sleep
[ 3210.608730] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 3210.610597] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 3210.610676] PM: Entering mem sleep
[ 3210.610702] Suspending console(s) (use no_console_suspend to debug)
[ 3210.670086] option: option_instat_callback: error -2
[ 3210.690275] btusb_bulk_complete: hci0 urb ffff88007652c000 failed to resubmit (1)
[ 3210.690407] btusb_bulk_complete: hci0 urb ffff88007652c240 failed to resubmit (1)
[ 3210.690458] btusb_intr_complete: hci0 urb ffff88007652c300 failed to resubmit (1)
[ 3210.810081] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 3210.810230] sd 0:0:0:0: [sda] Stopping disk
[ 3212.030370] ACPI handle has no context!
[ 3212.035479] ACPI handle has no context!
[ 3212.070190] iwlagn 0000:03:00.0: power state changed by ACPI to D3
[ 3212.070768] sky2 0000:02:00.0: PME# disabled
[ 3212.090259] sky2 0000:02:00.0: power state changed by ACPI to D3
[ 3212.090437] ata2: port disabled. ignoring.
[ 3212.090505] ata_piix 0000:00:1f.1: PCI INT B disabled
[ 3212.090568] ata_piix 0000:00:1f.1: power state changed by ACPI to D3
[ 3212.090583] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 3212.090594] uhci_hcd 0000:00:1d.3: PCI INT A disabled
[ 3212.090605] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 3212.090616] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 3212.090627] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 3212.200176] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 3212.266190] i915 0000:00:02.0: PCI INT A disabled
[ 3212.290207] PM: suspend devices took 1.680 seconds
[ 3212.290659] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3212.310986] ACPI: Preparing to enter system sleep state S3
[ 3213.010407] Disabling non-boot CPUs ...
[ 3213.120021] CPU 1 is now offline
[ 3213.120026] SMP alternatives: switching to UP code
[ 3213.132489] CPU0 attaching NULL sched-domain.
[ 3213.132495] CPU1 attaching NULL sched-domain.
[ 3213.132510] CPU0 attaching NULL sched-domain.
[ 3213.132849] CPU1 is down
[ 3213.132911] Extended CMOS year: 2000
[ 3213.132911] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 3213.132911] Back to C!
[ 3213.132911] CPU0: Thermal LVT vector (0xfa) already installed
[ 3213.132911] Extended CMOS year: 2000
[ 3213.132911] Enabling non-boot CPUs ...
[ 3213.132911] SMP alternatives: switching to SMP code
[ 3213.145230] Booting processor 1 APIC 0x1 ip 0x6000
[ 3213.132276] Initializing CPU#1
[ 3213.132276] Calibrating delay using timer specific routine.. 2128.10 BogoMIPS (lpj=10640536)
[ 3213.132276] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 3213.132276] CPU: L2 cache: 2048K
[ 3213.132276] CPU 1/0x1 -> Node 0
[ 3213.132276] CPU: Physical Processor ID: 0
[ 3213.132276] CPU: Processor Core ID: 1
[ 3213.132276] mce: CPU supports 6 MCE banks
[ 3213.132276] CPU1: Thermal monitoring enabled (TM2)
[ 3213.132276] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 3213.302165] CPU1: Intel(R) Core(TM)2 CPU         U7500  @ 1.06GHz stepping 02
[ 3213.302294] CPU0 attaching NULL sched-domain.
[ 3213.302525] Switched to high resolution mode on CPU 1
[ 3213.340036] CPU0 attaching sched-domain:
[ 3213.340042]  domain 0: span 0-1 level MC
[ 3213.340046]   groups: 0 1
[ 3213.340054] CPU1 attaching sched-domain:
[ 3213.340057]  domain 0: span 0-1 level MC
[ 3213.340061]   groups: 1 0
[ 3213.342527] CPU1 is up
[ 3213.342532] ACPI: Waking up from system sleep state S3
[ 3214.210189] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 3214.210238] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 3214.210297] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3214.210347] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[ 3214.210365] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f001)
[ 3214.210374] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf7f0f600)
[ 3214.210382] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[ 3214.210397] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 3214.210408] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3214.210475] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x4020a)
[ 3214.210494] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 3214.210502] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xfc00fc00)
[ 3214.210511] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[ 3214.210525] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 3214.210535] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3214.210602] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x4030a)
[ 3214.210620] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0xf3f1f201)
[ 3214.210629] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f800)
[ 3214.210637] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[ 3214.210651] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 3214.210662] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3214.210729] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x4040a)
[ 3214.210747] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf5f1f401)
[ 3214.210756] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xfbf0fa00)
[ 3214.210764] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0x4040)
[ 3214.210778] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 3214.210789] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3214.211051] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3214.211078] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0x83f18001)
[ 3214.211087] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xfc10fc10)
[ 3214.211095] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x228000f0, writing 0x22805050)
[ 3214.211776] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[ 3214.211813] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[ 3214.212024] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 3214.212137] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x2001)
[ 3214.212180] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6000004)
[ 3214.212208] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3214.212252] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3214.212568] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 3214.212628] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfc000004)
[ 3214.212641] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3214.212659] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 3214.212773] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xf (was 0x7000100, writing 0x5800100)
[ 3214.212782] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xe (was 0x0, writing 0x54fc)
[ 3214.212790] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xd (was 0x0, writing 0x5400)
[ 3214.212799] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xc (was 0x0, writing 0x50fc)
[ 3214.212807] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xb (was 0x0, writing 0x5000)
[ 3214.212815] yenta_cardbus 0000:09:04.0: restoring config space at offset 0xa (was 0x0, writing 0x87fff000)
[ 3214.212823] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x9 (was 0x0, writing 0x84000000)
[ 3214.212832] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x8 (was 0x0, writing 0x83fff000)
[ 3214.212840] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x7 (was 0x0, writing 0x80000000)
[ 3214.212849] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x6 (was 0x0, writing 0xb00d0a09)
[ 3214.212859] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xfc101000)
[ 3214.212868] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a800)
[ 3214.212878] yenta_cardbus 0000:09:04.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100007)
[ 3214.380034] ohci1394 0000:09:04.1: restoring config space at offset 0xf (was 0x4020200, writing 0x402020a)
[ 3214.380064] ohci1394 0000:09:04.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 3214.380075] ohci1394 0000:09:04.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 3214.380105] pci 0000:09:04.4: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[ 3214.380133] pci 0000:09:04.4: restoring config space at offset 0x4 (was 0x0, writing 0xfc100800)
[ 3214.380142] pci 0000:09:04.4: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 3214.380152] pci 0000:09:04.4: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 3214.556189] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3214.556198] i915 0000:00:02.0: setting latency timer to 64
[ 3214.617917] [drm] LVDS-8: set mode 1366x768 d
[ 3214.638519] pci 0000:00:02.1: PME# disabled
[ 3214.638532] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3214.638542] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 3214.638585] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3214.638595] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 3214.638627] usb usb2: root hub lost power or was reset
[ 3214.638667] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3214.638677] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 3214.638707] usb usb3: root hub lost power or was reset
[ 3214.638731] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[ 3214.638741] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3214.638770] usb usb4: root hub lost power or was reset
[ 3214.638794] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3214.638804] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 3214.638834] usb usb5: root hub lost power or was reset
[ 3214.638870] ehci_hcd 0000:00:1d.7: PME# disabled
[ 3214.638877] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 3214.638887] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3214.638922] pci 0000:00:1e.0: setting latency timer to 64
[ 3214.638938] ata_piix 0000:00:1f.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[ 3214.638946] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 3214.638991] sky2 0000:02:00.0: PME# disabled
[ 3214.640344] ata2: port disabled. ignoring.
[ 3214.702638] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fc100000-fc1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 3214.708771] pci 0000:09:04.4: PME# disabled
[ 3215.420541] sd 0:0:0:0: [sda] Starting disk
[ 3215.640537] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 3215.640543] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 3215.680830] ata1.00: configured for UDMA/100
[ 3215.800129] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[ 3216.240069] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[ 3216.520069] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[ 3216.732536] PM: resume devices took 2.350 seconds
[ 3216.732592] PM: Finishing wakeup.
[ 3216.732595] Restarting tasks ... done.
[ 3216.733494] usb 1-6.1: USB disconnect, address 8
[ 3216.733847] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 3216.733883] option 1-6.1:1.0: device disconnected
[ 3216.734128] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 3216.734159] option 1-6.1:1.1: device disconnected
[ 3216.734399] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 3216.734432] option 1-6.1:1.2: device disconnected
[ 3216.734667] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 3216.734700] option 1-6.1:1.3: device disconnected
[ 3217.018878] sky2 eth0: enabling interface
[ 3217.019388] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3217.235841] Registered led device: iwl-phy0::radio
[ 3217.235878] Registered led device: iwl-phy0::assoc
[ 3217.235913] Registered led device: iwl-phy0::RX
[ 3217.235945] Registered led device: iwl-phy0::TX
[ 3217.339806] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3218.110203] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[ 3218.127260] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[ 3222.442192] wlan0: authenticate with AP 00:1f:90:b3:3c:ac
[ 3222.444486] wlan0: authenticated
[ 3222.444492] wlan0: associate with AP 00:1f:90:b3:3c:ac
[ 3222.446802] wlan0: RX AssocResp from 00:1f:90:b3:3c:ac (capab=0x431 status=0 aid=2)
[ 3222.446808] wlan0: associated
[ 3222.470364] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3232.700038] wlan0: no IPv6 routers present
[ 4689.804285] [drm:edid_is_valid] *ERROR* Raw EDID:
[ 4689.804295] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804300] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804304] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804308] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804312] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804316] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804320] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804324] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 4689.804327] 
[ 4689.804332] i915 0000:00:02.0: LVDS-1: EDID invalid.
[ 4962.072578] CE: hpet increasing min_delta_ns to 33750 nsec
[12402.499447] hci_scodata_packet: hci0 SCO packet for unknown connection handle 46
[12402.499460] hci_scodata_packet: hci0 SCO packet for unknown connection handle 46
[12504.251806] hci_scodata_packet: hci0 SCO packet for unknown connection handle 47
[12504.251818] hci_scodata_packet: hci0 SCO packet for unknown connection handle 47
terry@terry-laptop:~$ 


```It's a lot, sorry, but I don't know what I should filter out.

---

### Post by chrisp_duck on 2009-11-26
I reckon 'dmesg | grep -i video' would have done it: -

> 
[   11.572522] usbcore: registered new interface driver uvcvideo
[   11.572528] USB Video Class driver (v0.1.0)


---

### Post by sexyclient2 on 2009-11-26
```
[    0.854338] pci 0000:00:02.0: Boot video device
[    1.519760] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input4
[    1.519839] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.329522] Linux video capture interface: v2.00
[   10.821669] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   11.568945] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[   11.572165] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   11.572420] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   11.572428] uvcvideo: Failed to initialize the device (-5).
[   11.572522] usbcore: registered new interface driver uvcvideo
[   11.572528] USB Video Class driver (v0.1.0)

```
Yes, much better.  There's a bit about the device failing to initialize, though, but it says the device is "registered" at the last line...  Could this, then, indeed be the problem that I'm having?

---

### Post by anonymousss on 2010-07-23
I had the exact same problem, were you able to solve it?

---

### Post by libssd on 2010-08-22
> **anonymousss said:**
> I had the exact same problem, were you able to solve it?
This appears to have happened to a number of people, but I have yet to see a solution. In my case, the webcam is failing under 4 different OS's (XP, 9.04, 10.04, Mint 9). I don't know if I have a hardware failure, or if something can be done to wake up the built-in webcam in my Acer netbook.

```

$ dmesg | grep uvcvideo
[   10.071244] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[   10.072110] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   10.072680] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   10.072692] uvcvideo: Failed to initialize the device (-5).
[   10.072796] usbcore: registered new interface driver uvcvideo
```
It's hard to believe that so many people would have webcam hardware failures on different brands, with what appear to be exactly the same symptoms. Yet, so far, I have been completely unable to find a way to make the webcam wake up.

There is a description of a fix here: [http://ubuntuforums.org/showthread.php?t=793513](http://ubuntuforums.org/showthread.php?t=793513)

But it's obsolete, in that it deals with Hardy, and makes reference to a subversion library that appears no longer to exist:

```
$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'
```

So, I'm back to square one. Inability to initialize the internal webcam seems to such a common problem across multiple brands of net/notebook computers and operating systems, that you would think there are some solutions out there (other than sending it in for repair). Since my problem exists under multiple different OS's, I am now leaning to a hardware problem that is unrelated to anything I did recently. I purchased a 1 year extended service contract when I bought the Acer, but of course, that expired about 60 days ago. I almost never use the webcam, so I am giving up on this problem until and if someone reports a workable solution.

---

### Post by libssd on 2010-08-22
This is becoming an obsession.

Output from lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1ea7:000b  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 007: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
So, the camera is definitely being detected on the USB bus, but won't initialize.

Detailed output from lsusb, section that appears to relate to the camera:

```
Bus 001 Device 007: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x0c45 Microdia
  idProduct          0x62c0 Sonix USB 2.0 Camera
  bcdDevice            1.00
  iManufacturer           2 Sonix Technology Co., Ltd.
  iProduct                1 WebCam
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          569
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               5 USB Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              5 USB Camera
```
What has to be done to initialize the camera? I'm beginning to feel like I have most of the necessary information, but I don't know how to apply it. I suspect it involves blacklisting a driver in /etc/modprobe.d/blacklist.conf, then enabling the appropriate driver for the Microdia camera somewhere else, possibly in /etc/rc.local. But the devil is in the details, which are currently beyond me.

---

### Post by hsoulen on 2010-08-23
Hey there,

Hope this helps: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

Good luck.

Hank

---

### Post by imercury on 2010-08-23
I installed the plugin for gmail video chat yesterday and the camera was detected. But today no camera detection ???

---

### Post by libssd on 2010-08-23
> **hsoulen said:**
> Hey there,

Hope this helps: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

Good luck.

Hank
Thanks. I tried that; still no camera function. Since the camera worked up until 2 weeks ago, and since it now doesn't work under any OS, hardware failure still seems like the most likely possibility. I know, from previous encounters with Acer that a repair would cost more than the netbook is worth. If loss of the camera really bothered me, I'd just get a newer, faster, longer running netbook, and transfer the SSD to the new machine.

---

### Post by libssd on 2010-08-29
Assuming this is a hardware problem (i.e., broken built-in webcam), but I don't care if the camera works or not, I blacklisted uvcvideo in /etc/modprobe.d/blacklist.conf. This stops the uvcvideo probe failed error message during boot.

Is there any reason I should **NOT** do this?

---

### Post by whatshisname on 2011-01-01
I've been getting this error message when using Motion with 2 Logictech C260 webcams running at the same time but only when I stop and restart motion.

The fix I've come up with is to manually remove the uvcvideo video driver with "rmmod uvcvideo" and then reload it with "modprobe uvcvideo".  Then restart motion.

I can then see both webcams using motion.

Hope this helps.

---

