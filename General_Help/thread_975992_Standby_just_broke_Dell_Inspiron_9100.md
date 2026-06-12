---
title: "Standby just broke Dell Inspiron 9100"
date: 2008-11-08
forum: General Help
---

### Post by Goombie on 2008-11-08
My standby function just broke yesterday, unfortunately. Before that it was working fine. I believe I installed a kernel update or something like that yesterday, but I can't remember. I also installed an update to qBittorrent yesterday, but I closed that before I tried to standby.
Here's the relevant portion of my syslog:
```

Nov  8 19:09:08 omlette-laptop NetworkManager: <info>  Going to sleep. 
Nov  8 19:09:08 omlette-laptop kernel: [40523.727924] wlan0: deauthenticate(reason=3)
Nov  8 19:09:08 omlette-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 9034
Nov  8 19:09:08 omlette-laptop dhclient: killed old client process, removed PID file
Nov  8 19:09:08 omlette-laptop dhclient: wmaster0: unknown hardware address type 801
Nov  8 19:09:08 omlette-laptop dhclient: wmaster0: unknown hardware address type 801
Nov  8 19:09:08 omlette-laptop dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Nov  8 19:09:08 omlette-laptop avahi-daemon[7088]: Withdrawing address record for 192.168.1.101 on wlan0.
Nov  8 19:09:08 omlette-laptop avahi-daemon[7088]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Nov  8 19:09:08 omlette-laptop avahi-daemon[7088]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  8 19:09:08 omlette-laptop kernel: [40524.379873] b43-phy0 debug: Removing Interface type 2
Nov  8 19:09:08 omlette-laptop kernel: [40524.487596] b43-phy0 debug: Wireless interface stopped
Nov  8 19:09:08 omlette-laptop kernel: [40524.487742] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 11/64
Nov  8 19:09:08 omlette-laptop kernel: [40524.487834] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
Nov  8 19:09:08 omlette-laptop kernel: [40524.495580] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
Nov  8 19:09:08 omlette-laptop kernel: [40524.503550] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
Nov  8 19:09:08 omlette-laptop kernel: [40524.511533] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
Nov  8 19:09:08 omlette-laptop kernel: [40524.519512] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 128/128
Nov  8 19:09:08 omlette-laptop kernel: [40524.527490] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
Nov  8 19:09:08 omlette-laptop avahi-daemon[7088]: Withdrawing address record for fe80::290:96ff:feb5:6e9b on wlan0.
Nov  8 19:09:09 omlette-laptop kernel: [40524.543663] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Nov  8 19:09:09 omlette-laptop NetworkManager: <debug> [1226200149.018081] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'). 
Nov  8 19:09:09 omlette-laptop NetworkManager: <debug> [1226200149.018201] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_65_ac_d3'). 
Nov  8 19:09:09 omlette-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  8 19:09:09 omlette-laptop kernel: [40524.688959] ACPI: PCI interrupt for device 0000:02:03.0 disabled
Nov  8 19:09:09 omlette-laptop NetworkManager: <debug> [1226200149.330360] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_90_96_b5_6e_9b'). 
Nov  8 19:09:09 omlette-laptop NetworkManager: <info>  Deactivating device wlan0. 
Nov  8 19:09:11 omlette-laptop kernel: [40526.690179] Syncing filesystems ... done.
Nov  8 19:09:11 omlette-laptop kernel: [40526.690236] PM: Preparing system for mem sleep
Nov  8 19:09:11 omlette-laptop kernel: [40526.690241] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov  8 19:09:11 omlette-laptop kernel: [40526.691157] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov  8 19:09:11 omlette-laptop kernel: [40526.691200] PM: Entering mem sleep
Nov  8 19:09:11 omlette-laptop kernel: [40526.691202] Suspending console(s)
Nov  8 19:09:11 omlette-laptop kernel: [40526.691211] sd 3:0:0:0: [sdb] Stopping disk
Nov  8 19:09:11 omlette-laptop kernel: [40526.648762] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.648768] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.648769]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.648772] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.648774] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.713498] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.713506] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.671034] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.671039] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.671040]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.671042] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.671043] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.737451] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.737456] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.694985] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.694989] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.694990]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.694992] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.694994] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.761392] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.761397] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.718926] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.718930] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.718931]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.718933] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.718935] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.785331] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.785336] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.742859] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.742863] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.742864]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.742866] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.742868] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.809282] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.809287] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.766809] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  8 19:09:11 omlette-laptop kernel: [40526.766814] ata4.00: cmd e0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov  8 19:09:11 omlette-laptop kernel: [40526.766815]          res 51/40:00:00:00:00/00:00:00:00:00/a0 Emask 0x9 (media error)
Nov  8 19:09:11 omlette-laptop kernel: [40526.766817] ata4.00: status: { DRDY ERR }
Nov  8 19:09:11 omlette-laptop kernel: [40526.766818] ata4.00: error: { UNC }
Nov  8 19:09:11 omlette-laptop kernel: [40526.833201] ata4.00: configured for PIO0
Nov  8 19:09:11 omlette-laptop kernel: [40526.833211] ata4: EH complete
Nov  8 19:09:11 omlette-laptop kernel: [40526.790371] sd 3:0:0:0: [sdb] START_STOP FAILED
Nov  8 19:09:11 omlette-laptop kernel: [40526.790374] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  8 19:09:11 omlette-laptop kernel: [40526.790379] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Nov  8 19:09:11 omlette-laptop kernel: [40526.790386] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Nov  8 19:09:11 omlette-laptop kernel: [40526.790395] suspend_device(): <5>sd 3:0:0:0: [sdb] 1985024 512-byte hardware sectors (1016 MB)
Nov  8 19:09:11 omlette-laptop kernel: [40526.790443] scsi_bus_suspend+0x0/0x50 [scsi_mod]() returns <5>sd 3:0:0:0: [sdb] Write Protect is off
Nov  8 19:09:11 omlette-laptop kernel: [40526.790448] 134217730
Nov  8 19:09:11 omlette-laptop kernel: [40526.833293] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 19:09:11 omlette-laptop kernel: [40526.790454] Could not suspend device 3:0:0:0: error 134217730
Nov  8 19:09:11 omlette-laptop kernel: [40526.790457] Some devices failed to suspend
Nov  8 19:09:11 omlette-laptop kernel: [40526.833334] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 19:09:11 omlette-laptop kernel: [40526.833379] sd 3:0:0:0: [sdb] 1985024 512-byte hardware sectors (1016 MB)
Nov  8 19:09:11 omlette-laptop kernel: [40526.833403] sd 3:0:0:0: [sdb] Write Protect is off
Nov  8 19:09:11 omlette-laptop kernel: [40526.833407] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 19:09:11 omlette-laptop kernel: [40526.833452] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 19:09:11 omlette-laptop kernel: [40526.791215] PM: Finishing wakeup.
Nov  8 19:09:11 omlette-laptop kernel: [40526.791218] Restarting tasks ... done.
Nov  8 19:09:11 omlette-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on wlan0: No such device 
Nov  8 19:09:11 omlette-laptop NetworkManager: <debug> [1226200151.770814] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_90_96_b5_6e_9b_0'). 
Nov  8 19:09:11 omlette-laptop NetworkManager: <debug> [1226200151.770914] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:11 omlette-laptop NetworkManager: <debug> [1226200151.770980] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:11 omlette-laptop NetworkManager: <debug> [1226200151.771045] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:11 omlette-laptop NetworkManager: <debug> [1226200151.771109] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:15 omlette-laptop anacron[32123]: Anacron 2.3 started on 2008-11-08
Nov  8 19:09:15 omlette-laptop anacron[32123]: Normal exit (0 jobs run)
Nov  8 19:09:15 omlette-laptop kernel: [40530.927310] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 17
Nov  8 19:09:15 omlette-laptop kernel: [40530.927352] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40530.927361] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40530.927371] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40530.927382] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40530.927391] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40530.930791] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
Nov  8 19:09:15 omlette-laptop kernel: [40530.967670] b43-phy0: Broadcom 4306 WLAN found
Nov  8 19:09:15 omlette-laptop kernel: [40530.991353] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
Nov  8 19:09:15 omlette-laptop kernel: [40530.991379] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
Nov  8 19:09:15 omlette-laptop NetworkManager: <debug> [1226200155.259343] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:15 omlette-laptop kernel: [40531.027204] phy0: Selected rate control algorithm 'simple'
Nov  8 19:09:15 omlette-laptop NetworkManager: <debug> [1226200155.273962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:15 omlette-laptop NetworkManager: <debug> [1226200155.288709] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_90_96_b5_6e_9b'). 
Nov  8 19:09:15 omlette-laptop NetworkManager: <debug> [1226200155.296976] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_90_96_b5_6e_9b_0'). 
Nov  8 19:09:15 omlette-laptop kernel: [40531.093837] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Nov  8 19:09:15 omlette-laptop kernel: [40531.102954] input: b43-phy0 as /devices/virtual/input/input12
Nov  8 19:09:15 omlette-laptop kernel: [40531.153914] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40531.153929] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40531.153938] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
Nov  8 19:09:15 omlette-laptop kernel: [40531.198836] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
Nov  8 19:09:15 omlette-laptop kernel: [40531.198881] b44.c:v2.0
Nov  8 19:09:15 omlette-laptop kernel: [40531.409840] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Nov  8 19:09:17 omlette-laptop kernel: [40532.894070] b43-phy0 debug: Chip initialized
Nov  8 19:09:17 omlette-laptop kernel: [40532.894317] b43-phy0 debug: 30-bit DMA initialized
Nov  8 19:09:17 omlette-laptop kernel: [40532.894702] Registered led device: b43-phy0:tx
Nov  8 19:09:17 omlette-laptop kernel: [40532.894733] Registered led device: b43-phy0:rx
Nov  8 19:09:17 omlette-laptop kernel: [40532.894765] Registered led device: b43-phy0:radio
Nov  8 19:09:17 omlette-laptop kernel: [40532.894795] b43-phy0 debug: Wireless interface started
Nov  8 19:09:17 omlette-laptop kernel: [40532.933708] b43-phy0 debug: Adding Interface type 2
Nov  8 19:09:17 omlette-laptop kernel: [40532.938277] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  8 19:09:17 omlette-laptop kernel: [40532.957648] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:43:65:ac:d3
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'b43'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Deactivating device wlan0. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <debug> [1226200157.164661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:17 omlette-laptop NetworkManager: <debug> [1226200157.165713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'). 
Nov  8 19:09:17 omlette-laptop NetworkManager: <debug> [1226200157.166730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Nov  8 19:09:17 omlette-laptop NetworkManager: <debug> [1226200157.175937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_43_65_ac_d3'). 
Nov  8 19:09:17 omlette-laptop kernel: [40532.996282] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Waking up from sleep. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Deactivating device wlan0. 
Nov  8 19:09:17 omlette-laptop kernel: [40533.121994] b43-phy0 debug: Removing Interface type 2
Nov  8 19:09:17 omlette-laptop kernel: [40533.221926] b43-phy0 debug: Wireless interface stopped
Nov  8 19:09:17 omlette-laptop kernel: [40533.222080] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
Nov  8 19:09:17 omlette-laptop kernel: [40533.222158] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop kernel: [40533.229953] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop kernel: [40533.237933] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop kernel: [40533.245665] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop kernel: [40533.253651] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop kernel: [40533.261611] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  8 19:09:17 omlette-laptop kernel: [40533.272382] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov  8 19:09:17 omlette-laptop NetworkManager: <info>  Deactivating device eth0. 
Nov  8 19:09:17 omlette-laptop kernel: [40533.341447] input: b43-phy0 as /devices/virtual/input/input13
Nov  8 19:09:17 omlette-laptop kernel: [40533.468271] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Nov  8 19:09:18 omlette-laptop kernel: [40534.254900] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov  8 19:09:18 omlette-laptop kernel: [40534.254925] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov  8 19:09:18 omlette-laptop kernel: [40534.254966] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov  8 19:09:18 omlette-laptop kernel: [40534.254997] [drm] Loading R300 Microcode
Nov  8 19:09:19 omlette-laptop kernel: [40535.012497] b43-phy0 debug: Chip initialized
Nov  8 19:09:19 omlette-laptop kernel: [40535.012725] b43-phy0 debug: 30-bit DMA initialized
Nov  8 19:09:19 omlette-laptop kernel: [40535.013105] Registered led device: b43-phy0:tx
Nov  8 19:09:19 omlette-laptop kernel: [40535.013309] Registered led device: b43-phy0:rx
Nov  8 19:09:19 omlette-laptop kernel: [40535.013512] Registered led device: b43-phy0:radio
Nov  8 19:09:19 omlette-laptop kernel: [40535.013551] b43-phy0 debug: Wireless interface started
Nov  8 19:09:19 omlette-laptop kernel: [40535.060376] b43-phy0 debug: Adding Interface type 2
Nov  8 19:09:19 omlette-laptop kernel: [40535.064951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'b44'. 
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Nov  8 19:09:19 omlette-laptop NetworkManager: <info>  Deactivating device wlan0. 
Nov  8 19:09:19 omlette-laptop NetworkManager: <debug> [1226200159.280385] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'). 
Nov  8 19:09:19 omlette-laptop NetworkManager: <debug> [1226200159.281130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'). 
Nov  8 19:09:21 omlette-laptop gnome-power-manager: (omlette) Resuming computer

```Near as I can tell, the problem seems to be with something called 'ata4', but I don't know how to find out what that is, or how to fix this problem.
If anyone could help, that would be great! :popcorn:

---

