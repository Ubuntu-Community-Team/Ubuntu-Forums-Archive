---
title: "Help interpret log file"
date: 2008-12-15
forum: Hardware
---

### Post by gravyflex on 2008-12-15
I am seeking help figuring out these event in my dmesg log file. I suspect that my hard drive is failing. I am trying to figure out if there are any corrective actions I can take to stop theres errors or is it a lost cause?

```

[   44.692512] EXT3 FS on sda7, internal journal
[   46.016106] kjournald starting.  Commit interval 5 seconds
[   46.017060] EXT3 FS on sda6, internal journal
[   46.017071] EXT3-fs: mounted filesystem with ordered data mode.
[   46.903629] type=1505 audit(1229400206.506:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3681
[   46.904246] type=1505 audit(1229400206.510:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3681
[   46.995881] type=1505 audit(1229400206.598:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3685
[   47.325651] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.538289] eth1: New link status: Connected (0001)
[   48.877217] NET: Registered protocol family 17
[   52.537209] eth2:  setting half-duplex.
[   53.918605] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[  129.010305] ACPI: WMI: Mapper loaded
[  131.848318] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  131.848335] ata1.00: BMDMA stat 0x25
[  131.848346] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  131.848349]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  131.848356] ata1.00: status: { DRDY ERR }
[  131.848360] ata1.00: error: { UNC }
[  131.872484] ata1.00: configured for UDMA/100
[  131.872511] ata1: EH complete
[  133.901263] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.901275] ata1.00: BMDMA stat 0x25
[  133.901284] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  133.901287]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  133.901293] ata1.00: status: { DRDY ERR }
[  133.901297] ata1.00: error: { UNC }
[  133.924527] ata1.00: configured for UDMA/100
[  133.924547] ata1: EH complete
[  135.968486] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  135.968498] ata1.00: BMDMA stat 0x25
[  135.968507] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  135.968510]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  135.968516] ata1.00: status: { DRDY ERR }
[  135.968520] ata1.00: error: { UNC }
[  135.992541] ata1.00: configured for UDMA/100
[  135.992561] ata1: EH complete
[  138.064212] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  138.064224] ata1.00: BMDMA stat 0x25
[  138.064233] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  138.064236]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  138.064242] ata1.00: status: { DRDY ERR }
[  138.064245] ata1.00: error: { UNC }
[  138.088533] ata1.00: configured for UDMA/100
[  138.088552] ata1: EH complete
[  140.202719] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  140.202732] ata1.00: BMDMA stat 0x25
[  140.202742] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  140.202744]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  140.202750] ata1.00: status: { DRDY ERR }
[  140.202754] ata1.00: error: { UNC }
[  140.224522] ata1.00: configured for UDMA/100
[  140.224544] ata1: EH complete
[  142.255658] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  142.255670] ata1.00: BMDMA stat 0x25
[  142.255679] ata1.00: cmd c8/00:08:07:88:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  142.255682]          res 51/40:05:0a:88:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  142.255687] ata1.00: status: { DRDY ERR }
[  142.255691] ata1.00: error: { UNC }
[  142.276546] ata1.00: configured for UDMA/100
[  142.276576] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  142.276584] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  142.276594] Descriptor sense data with sense descriptors (in hex):
[  142.276599]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  142.276617]         02 10 88 0a 
[  142.276624] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  142.276635] end_request: I/O error, dev sda, sector 34637834
[  142.276670] ata1: EH complete
[  142.297036] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  142.297101] sd 0:0:0:0: [sda] Write Protect is off
[  142.297107] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  142.297194] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  142.297279] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  142.297322] sd 0:0:0:0: [sda] Write Protect is off
[  142.297327] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  142.297402] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.776070] Clocksource tsc unstable (delta = -125197115 ns)
[  161.387840] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  161.387863] ata1.00: BMDMA stat 0x25
[  161.387879] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  161.387884]          res 51/40:0e:59:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  161.387893] ata1.00: status: { DRDY ERR }
[  161.387898] ata1.00: error: { UNC }
[  161.416592] ata1.00: configured for UDMA/100
[  161.416624] ata1: EH complete
[  163.383709] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  163.383728] ata1.00: BMDMA stat 0x25
[  163.383742] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  163.383746]          res 51/40:0e:59:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  163.383754] ata1.00: status: { DRDY ERR }
[  163.383760] ata1.00: error: { UNC }
[  163.404585] ata1.00: configured for UDMA/100
[  163.404619] ata1: EH complete
[  165.393847] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  165.393865] ata1.00: BMDMA stat 0x25
[  165.393879] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  165.393883]          res 51/40:0e:59:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  165.393891] ata1.00: status: { DRDY ERR }
[  165.393896] ata1.00: error: { UNC }
[  165.416563] ata1.00: configured for UDMA/100
[  165.416596] ata1: EH complete
[  167.774666] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  167.774792] ata1.00: BMDMA stat 0x25
[  167.774892] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  167.774896]          res 51/40:0d:5a:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  167.775114] ata1.00: status: { DRDY ERR }
[  167.775202] ata1.00: error: { UNC }
[  167.796586] ata1.00: configured for UDMA/100
[  167.796626] ata1: EH complete
[  169.770524] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  169.770630] ata1.00: BMDMA stat 0x25
[  169.770722] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  169.770726]          res 51/40:0d:5a:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  169.770944] ata1.00: status: { DRDY ERR }
[  169.771028] ata1.00: error: { UNC }
[  169.792593] ata1.00: configured for UDMA/100
[  169.792628] ata1: EH complete
[  171.809173] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  171.809283] ata1.00: BMDMA stat 0x25
[  171.809374] ata1.00: cmd c8/00:10:57:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  171.809378]          res 51/40:0d:5a:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  171.809589] ata1.00: status: { DRDY ERR }
[  171.809673] ata1.00: error: { UNC }
[  171.832554] ata1.00: configured for UDMA/100
[  171.832596] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  171.832607] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  171.832620] Descriptor sense data with sense descriptors (in hex):
[  171.832626]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  171.832650]         02 0e 95 5a 
[  171.832660] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  171.832675] end_request: I/O error, dev sda, sector 34510170
[  171.832806] ata1: EH complete
[  171.833866] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  174.521513] sd 0:0:0:0: [sda] Write Protect is off
[  174.521533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  174.522590] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  174.524333] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  174.540806] sd 0:0:0:0: [sda] Write Protect is off
[  174.540824] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  174.610380] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  177.468914] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  177.469026] ata1.00: BMDMA stat 0x25
[  177.469125] ata1.00: cmd c8/00:10:87:95:0e/00:00:00:00:00/e2 tag 0 dma 8192 in
[  177.469129]          res 51/40:02:95:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  177.469339] ata1.00: status: { DRDY ERR }
[  177.469428] ata1.00: error: { UNC }
[  177.492558] ata1.00: configured for UDMA/100
[  177.492592] ata1: EH complete
[  181.757223] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  181.799307] sd 0:0:0:0: [sda] Write Protect is off
[  181.799324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  181.799450] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  184.810870] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  184.810980] ata1.00: BMDMA stat 0x25
[  184.811079] ata1.00: cmd c8/00:20:97:95:0e/00:00:00:00:00/e2 tag 0 dma 16384 in
[  184.811083]          res 51/40:1a:9d:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  184.811293] ata1.00: status: { DRDY ERR }
[  184.811380] ata1.00: error: { UNC }
[  184.832523] ata1.00: configured for UDMA/100
[  184.832556] ata1: EH complete
[  186.977800] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  186.977906] ata1.00: BMDMA stat 0x25
[  186.977997] ata1.00: cmd c8/00:20:97:95:0e/00:00:00:00:00/e2 tag 0 dma 16384 in
[  186.978001]          res 51/40:20:97:95:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  186.978208] ata1.00: status: { DRDY ERR }
[  186.978292] ata1.00: error: { UNC }
[  187.000523] ata1.00: configured for UDMA/100
[  187.000557] ata1: EH complete
[  187.569696] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  187.570459] sd 0:0:0:0: [sda] Write Protect is off
[  187.570479] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  187.570612] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  187.570735] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  187.570800] sd 0:0:0:0: [sda] Write Protect is off
[  187.570807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  187.570917] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  190.442065] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  190.442175] ata1.00: BMDMA stat 0x25
[  190.442269] ata1.00: cmd c8/00:08:cf:9a:0e/00:00:00:00:00/e2 tag 0 dma 4096 in
[  190.442274]          res 51/40:01:d6:9a:0e/00:00:00:00:00/e2 Emask 0x9 (media error)
[  190.442480] ata1.00: status: { DRDY ERR }
[  190.442571] ata1.00: error: { UNC }
[  190.464615] ata1.00: configured for UDMA/100
[  190.464652] ata1: EH complete
[  190.841568] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  190.844222] sd 0:0:0:0: [sda] Write Protect is off
[  190.844247] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.925380] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  193.119422] eth1: New link status: Connected (0001)
[  193.163646] eth1: New link status: Disconnected (0002)
[  193.325737] eth1: New link status: Connected (0001)
[  196.064956] Bluetooth: Core ver 2.13
[  196.070080] NET: Registered protocol family 31
[  196.070097] Bluetooth: HCI device and connection manager initialized
[  196.070106] Bluetooth: HCI socket layer initialized
[  196.237611] Bluetooth: L2CAP ver 2.11
[  196.237627] Bluetooth: L2CAP socket layer initialized
[  196.373527] Bluetooth: SCO (Voice Link) ver 0.6
[  196.373548] Bluetooth: SCO socket layer initialized
[  196.423283] Bluetooth: RFCOMM socket layer initialized
[  196.442955] Bluetooth: RFCOMM TTY layer initialized
[  196.442984] Bluetooth: RFCOMM ver 1.10
[  196.467199] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  196.467215] Bluetooth: BNEP filters: protocol multicast
[  198.502260] Bridge firewalling registered
[  198.505713] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  205.567813] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  205.567834] ata1.00: BMDMA stat 0x25
[  205.567848] ata1.00: cmd c8/00:08:2f:d6:0b/00:00:00:00:00/e2 tag 0 dma 4096 in
[  205.567852]          res 51/40:08:2f:d6:0b/00:00:00:00:00/e2 Emask 0x9 (media error)
[  205.567861] ata1.00: status: { DRDY ERR }
[  205.567866] ata1.00: error: { UNC }
[  205.596602] ata1.00: configured for UDMA/100
[  205.596636] ata1: EH complete
[  208.005601] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  208.005621] ata1.00: BMDMA stat 0x25
[  208.005638] ata1.00: cmd c8/00:08:2f:d6:0b/00:00:00:00:00/e2 tag 0 dma 4096 in
[  208.005642]          res 51/40:07:30:d6:0b/00:00:00:00:00/e2 Emask 0x9 (media error)
[  208.005650] ata1.00: status: { DRDY ERR }
[  208.005655] ata1.00: error: { UNC }
[  208.036609] ata1.00: configured for UDMA/100
[  208.036650] ata1: EH complete
[  210.072706] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  210.072725] ata1.00: BMDMA stat 0x25
[  210.072740] ata1.00: cmd c8/00:08:2f:d6:0b/00:00:00:00:00/e2 tag 0 dma 4096 in
[  210.072743]          res 51/40:07:30:d6:0b/00:00:00:00:00/e2 Emask 0x9 (media error)
[  210.072751] ata1.00: status: { DRDY ERR }
[  210.072756] ata1.00: error: { UNC }
[  210.096592] ata1.00: configured for UDMA/100
[  210.096631] ata1: EH complete
[  211.573829] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  211.573908] sd 0:0:0:0: [sda] Write Protect is off
[  211.573916] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  211.574029] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  211.574150] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  211.574213] sd 0:0:0:0: [sda] Write Protect is off
[  211.574221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  211.574333] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  252.384240] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  252.384262] ata1.00: BMDMA stat 0x25
[  252.384277] ata1.00: cmd c8/00:08:6f:15:d2/00:00:00:00:00/e1 tag 0 dma 4096 in
[  252.384281]          res 51/40:08:6f:15:d2/00:00:00:00:00/e1 Emask 0x9 (media error)
[  252.384289] ata1.00: status: { DRDY ERR }
[  252.384297] ata1.00: error: { UNC }
[  252.416590] ata1.00: configured for UDMA/100
[  252.416625] ata1: EH complete
[  252.996923] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  252.997005] sd 0:0:0:0: [sda] Write Protect is off
[  252.997013] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  253.020070] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  368.286901] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  368.286924] ata1.00: BMDMA stat 0x25
[  368.286939] ata1.00: cmd c8/00:08:c7:7d:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  368.286943]          res 51/40:04:cb:7d:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  368.286952] ata1.00: status: { DRDY ERR }
[  368.286960] ata1.00: error: { UNC }
[  368.308545] ata1.00: configured for UDMA/100
[  368.308571] ata1: EH complete
[  370.424092] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  370.424104] ata1.00: BMDMA stat 0x25
[  370.424119] ata1.00: cmd c8/00:08:c7:7d:10/00:00:00:00:00/e2 tag 0 dma 4096 in
[  370.424123]          res 51/40:08:c7:7d:10/00:00:00:00:00/e2 Emask 0x9 (media error)
[  370.424132] ata1.00: status: { DRDY ERR }
[  370.424138] ata1.00: error: { UNC }
[  370.448526] ata1.00: configured for UDMA/100
[  370.448550] ata1: EH complete
[  373.210827] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  373.212642] sd 0:0:0:0: [sda] Write Protect is off
[  373.212650] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  373.212878] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  373.213001] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors (20004 MB)
[  373.213059] sd 0:0:0:0: [sda] Write Protect is off
[  373.213067] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  373.213165] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


```

---

### Post by cdtech on 2008-12-15
Try running the smartctl on the drive and see what it say's:
```
smartctl -a /dev/sda
```

---

### Post by tommcd on 2008-12-15
Install the **smartmontools** package to get **smartctl**.

---

