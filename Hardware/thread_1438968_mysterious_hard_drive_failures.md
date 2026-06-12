---
title: "mysterious hard drive failures"
date: 2010-03-25
forum: Hardware
---

### Post by McButt on 2010-03-25
hey all, 
I've been having some weird hard drive failures on my mythtv/torrent computer, running a normal 9.10 ubuntu install. Hopefully someone here can tell me what's going on with this thing. The error seems to occur after the thing has been on for at least 1-2 days. The most recent occurrence didn't do any damage and was fixed by a reboot (and turning off the power supply for a moment), but other times I've had to run fsck to restore the data.
This is the syslog from the point where it goes wrong.
```
Mar 25 20:28:00 mythbox kernel: [143896.968589] ata1: lost interrupt (Status 0x50)
Mar 25 20:28:00 mythbox kernel: [143896.968619] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar 25 20:28:00 mythbox kernel: [143896.968635] ata1.00: cmd c8/00:28:98:d0:0a/00:00:00:00:00/e3 tag 0 dma 20480 in
Mar 25 20:28:00 mythbox kernel: [143896.968638]          res 40/00:00:00:4f:c2/00:00:00:00:00/10 Emask 0x4 (timeout)
Mar 25 20:28:00 mythbox kernel: [143896.968643] ata1.00: status: { DRDY }
Mar 25 20:28:00 mythbox kernel: [143896.968676] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143897.141186] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.141196] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.157046] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143897.189005] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143897.189016] ata1.00: device reported invalid CHS sector 0
Mar 25 20:28:00 mythbox kernel: [143897.189028] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143897.595158] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143897.595166] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143897.595180] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143897.595183]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143897.595188] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143897.595192] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143897.595225] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143897.765194] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.765204] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.781087] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143897.822273] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143897.822293] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143897.893650] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143897.893657] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143897.893670] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143897.893673]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143897.893678] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143897.893682] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143897.893715] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.065244] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.065254] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.081304] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.121085] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143898.121105] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.192136] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.192144] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.192157] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.192159]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.192165] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.192169] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.192201] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.361507] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.361517] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.377147] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.424776] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143898.424797] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.490623] ata1.01: limiting speed to UDMA/66:PIO4
Mar 25 20:28:00 mythbox kernel: [143898.490632] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.490638] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.490651] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.490654]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.490659] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.490663] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.490696] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.661741] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.661751] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.677165] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.717136] ata1.01: configured for UDMA/66
Mar 25 20:28:00 mythbox kernel: [143898.717156] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.780812] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.780820] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.780833] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.780835]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.780841] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.780844] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.780877] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.953284] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.953293] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.969228] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143899.009471] ata1.01: configured for UDMA/66
Mar 25 20:28:00 mythbox kernel: [143899.009492] ata1: EH complete
Mar 25 20:30:01 mythbox CRON[15058]: (piet) CMD (/usr/local/bin/flexget     #Leest rss feed van torrent tracker en voegt gewenste torrents toe aan deluge)
Mar 25 20:30:01 mythbox CRON[15060]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:30:10 mythbox kernel: [144029.518076] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:30:10 mythbox kernel: [144029.518085] ata1.01: BMDMA stat 0x64
Mar 25 20:30:10 mythbox kernel: [144029.518098] ata1.01: cmd c8/00:60:e7:5e:59/00:00:00:00:00/f4 tag 0 dma 49152 in
Mar 25 20:30:10 mythbox kernel: [144029.518101]          res 51/84:00:46:5f:59/84:00:11:00:00/f4 Emask 0x10 (ATA bus error)
Mar 25 20:30:10 mythbox kernel: [144029.518156] ata1.01: status: { DRDY ERR }
Mar 25 20:30:10 mythbox kernel: [144029.518172] ata1.01: error: { ICRC ABRT }
Mar 25 20:30:10 mythbox kernel: [144029.518206] ata1: soft resetting link
Mar 25 20:30:11 mythbox kernel: [144029.689089] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:30:11 mythbox kernel: [144029.689098] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:30:11 mythbox kernel: [144029.705607] ata1.00: configured for UDMA/133
Mar 25 20:30:11 mythbox kernel: [144029.736953] ata1.01: configured for UDMA/66
Mar 25 20:30:11 mythbox kernel: [144029.736973] ata1: EH complete
Mar 25 20:30:17 mythbox sensord: Chip: it8712-isa-0290
Mar 25 20:30:17 mythbox sensord: Adapter: ISA adapter
Mar 25 20:30:17 mythbox sensord:   VCore 1: +1.30 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   VCore 2: +1.50 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   +3.3V: +3.07 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   +5V: +5.00 V (min = +0.00 V, max = +6.85 V)
Mar 25 20:30:17 mythbox sensord:   +12V: +11.97 V (min = +0.00 V, max = +16.32 V)
Mar 25 20:30:17 mythbox sensord:   -12V: -20.12 V (min = -27.36 V, max = +3.93 V)
Mar 25 20:30:17 mythbox sensord:   -5V: -6.30 V (min = -13.64 V, max = +4.03 V)
Mar 25 20:30:17 mythbox sensord:   Stdby: +4.95 V (min = +0.00 V, max = +6.85 V)
Mar 25 20:30:17 mythbox sensord:   VBat: +4.08 V
Mar 25 20:30:17 mythbox sensord:   fan1: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   fan2: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   fan3: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   M/B Temp: 33.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   CPU Temp: 37.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   Temp3: 34.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   cpu0_vid: +0.000 V
Mar 25 20:31:15 mythbox kernel: [144094.204595] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:31:15 mythbox kernel: [144094.204604] ata1.01: BMDMA stat 0x64
Mar 25 20:31:15 mythbox kernel: [144094.204617] ata1.01: cmd 25/00:00:f7:d5:91/00:02:0d:00:00/f0 tag 0 dma 262144 in
Mar 25 20:31:15 mythbox kernel: [144094.204619]          res 51/84:00:f6:d7:91/84:00:0d:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:31:15 mythbox kernel: [144094.204625] ata1.01: status: { DRDY ERR }
Mar 25 20:31:15 mythbox kernel: [144094.204629] ata1.01: error: { ICRC ABRT }
Mar 25 20:31:15 mythbox kernel: [144094.204661] ata1: soft resetting link
Mar 25 20:31:15 mythbox kernel: [144094.374921] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:15 mythbox kernel: [144094.374931] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:15 mythbox kernel: [144094.390821] ata1.00: configured for UDMA/133
Mar 25 20:31:15 mythbox kernel: [144094.430457] ata1.01: configured for UDMA/66
Mar 25 20:31:15 mythbox kernel: [144094.430477] ata1: EH complete
Mar 25 20:31:15 mythbox kernel: [144094.453279] ata1.01: limiting speed to UDMA/33:PIO4
Mar 25 20:31:15 mythbox kernel: [144094.453289] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:31:15 mythbox kernel: [144094.453295] ata1.01: BMDMA stat 0x64
Mar 25 20:31:15 mythbox kernel: [144094.453308] ata1.01: cmd 25/00:00:f7:d5:91/00:02:0d:00:00/f0 tag 0 dma 262144 in
Mar 25 20:31:15 mythbox kernel: [144094.453311]          res 51/84:00:f6:d7:91/84:00:0d:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:31:15 mythbox kernel: [144094.453316] ata1.01: status: { DRDY ERR }
Mar 25 20:31:15 mythbox kernel: [144094.453320] ata1.01: error: { ICRC ABRT }
Mar 25 20:31:15 mythbox kernel: [144094.453353] ata1: soft resetting link
Mar 25 20:31:16 mythbox kernel: [144094.623273] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:16 mythbox kernel: [144094.623283] ata1: nv_mode_filter: 0x739f&0x3f3ff->0x739f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:16 mythbox kernel: [144094.640297] ata1.00: configured for UDMA/133
Mar 25 20:31:16 mythbox kernel: [144094.678644] ata1.01: model number mismatch 'SAMSUNG SP2014N' != 'CAMSENG CP"0!4N'
Mar 25 20:31:16 mythbox kernel: [144094.678651] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:16 mythbox kernel: [144094.678662] ata1.01: limiting speed to UDMA/33:PIO3
Mar 25 20:31:21 mythbox kernel: [144099.606874] ata1: soft resetting link
Mar 25 20:31:21 mythbox kernel: [144099.771192] ata1.01: model number mismatch 'SAMSUNG SP2014N' != 'SAMSENG CP"0!4N'
Mar 25 20:31:21 mythbox kernel: [144099.771199] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:21 mythbox kernel: [144099.771206] ata1.01: disabled
Mar 25 20:31:26 mythbox kernel: [144104.763343] ata1: soft resetting link
Mar 25 20:31:27 mythbox kernel: [144105.535942] ata1.01: ATA-7: SAMSUNG CP"014N, VC100-$1, max UDMA/100
Mar 25 20:31:27 mythbox kernel: [144105.535949] ata1.01: 390721968 sectors, multi 16: LBA48 
Mar 25 20:31:27 mythbox kernel: [144105.535985] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:27 mythbox kernel: [144105.535993] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:27 mythbox kernel: [144105.551965] ata1.00: configured for UDMA/133
Mar 25 20:31:27 mythbox kernel: [144105.583624] ata1.01: model number mismatch 'SAMSUNG CP"014N' != 'SAMSUNG SP2014N'
Mar 25 20:31:27 mythbox kernel: [144105.583632] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:27 mythbox kernel: [144105.583643] ata1.01: limiting speed to UDMA/100:PIO3
Mar 25 20:31:31 mythbox kernel: [144109.919802] ata1: soft resetting link
Mar 25 20:31:31 mythbox kernel: [144110.084114] ata1.01: model number mismatch 'SAMSUNG CP"014N' != 'SAMSUNG SP2014N'
Mar 25 20:31:31 mythbox kernel: [144110.084121] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:31 mythbox kernel: [144110.084128] ata1.01: disabled
Mar 25 20:31:31 mythbox kernel: [144110.092333] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:31 mythbox kernel: [144110.108624] ata1.00: configured for UDMA/133
Mar 25 20:31:31 mythbox kernel: [144110.108653] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 25 20:31:31 mythbox kernel: [144110.108660] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Mar 25 20:31:31 mythbox kernel: [144110.108667] Descriptor sense data with sense descriptors (in hex):
Mar 25 20:31:31 mythbox kernel: [144110.108671]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 25 20:31:31 mythbox kernel: [144110.108683]         0d 91 d7 f6 
Mar 25 20:31:31 mythbox kernel: [144110.108689] sd 0:0:1:0: [sdb] Add. Sense: Scsi parity error
Mar 25 20:31:31 mythbox kernel: [144110.108699] end_request: I/O error, dev sdb, sector 227661303
Mar 25 20:31:31 mythbox kernel: [144110.108738] ata1: EH complete
Mar 25 20:31:31 mythbox kernel: [144110.108900] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.161346] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.161388] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162096] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162126] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162305] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162324] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162339] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162621] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162674] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162693] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162708] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.257078] ata1.01: detaching (SCSI 0:0:1:0)
Mar 25 20:31:32 mythbox kernel: [144110.624546] sd 0:0:1:0: [sdb] Synchronizing SCSI cache
Mar 25 20:31:32 mythbox kernel: [144110.628991] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 25 20:31:32 mythbox kernel: [144110.629002] sd 0:0:1:0: [sdb] Stopping disk
Mar 25 20:31:32 mythbox kernel: [144110.629018] sd 0:0:1:0: [sdb] START_STOP FAILED
Mar 25 20:31:32 mythbox kernel: [144110.629022] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 25 20:31:32 mythbox kernel: [144110.962185] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144110.962200] Aborting journal on device sdb1.
Mar 25 20:31:32 mythbox kernel: [144110.962218] Remounting filesystem read-only
Mar 25 20:31:32 mythbox kernel: [144111.097743] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.097864] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.097965] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098062] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098157] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098252] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.101238] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102070] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102506] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102627] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102725] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.104982] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.105466] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.240492] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.241258] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267593] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267768] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267869] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.268835] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269074] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269275] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269381] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269477] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269575] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269671] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269766] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269862] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269956] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270052] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270146] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270242] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270339] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270434] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270529] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270623] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270718] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270813] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270908] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271003] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271098] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271193] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271288] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271383] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271477] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271572] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271667] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271762] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278089] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278543] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278873] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279337] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279590] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279850] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.280000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.280339] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.282401] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.282794] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283046] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283287] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283526] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283763] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283917] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284026] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284124] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284221] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284316] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284412] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284508] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284604] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284699] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284795] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284890] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.285013] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.288897] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289254] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289561] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289809] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290049] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290313] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290527] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290767] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290895] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290999] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291095] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291189] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291283] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291377] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291471] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291565] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291660] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291753] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291847] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291974] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292256] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292377] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292474] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292570] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292665] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292760] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292854] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292949] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293062] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293157] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293253] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293348] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293443] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293537] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293632] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293727] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.301148] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.301463] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.302479] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.303632] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304022] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304364] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304617] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304854] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305118] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305361] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305568] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305700] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305810] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305910] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306024] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306122] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306219] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306316] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306481] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306577] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.309418] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362064] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362319] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362419] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362515] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.713871] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.760781] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.760940] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761042] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761210] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761326] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761424] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761523] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761622] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761720] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761817] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761915] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762028] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762125] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762223] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762320] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762417] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762514] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762610] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:35:01 mythbox CRON[15136]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:38:14 mythbox kernel: [144512.991085] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.018880] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.019175] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.019435] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:49 mythbox kernel: [144547.549345] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:39:01 mythbox CRON[15196]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 25 20:40:01 mythbox CRON[15208]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:40:01 mythbox CRON[15214]: (piet) CMD (/usr/local/bin/flexget     #Leest rss feed van torrent tracker en voegt gewenste torrents toe aan deluge)
Mar 25 20:43:07 mythbox kernel: [144805.761193] ext3_abort called.
Mar 25 20:43:07 mythbox kernel: [144805.761202] EXT3-fs error (device sdb1): ext3_put_super: Couldn't clean up the journal
```
Apparently the controller loses connection to the two hard drives and fails to restore it to one of them. This time it was the drive that only contains data, but I suspect it's been happening to the system drive as well because I've had two mysterious system crashes this month.
I don't think the drives are faulty, since they've always worked well in my main computer before being handed down to this one. Also if the drive fails you wouldn't expect it to be recovered on reboot, right?
Any ideas on what's going on here?

---

### Post by quixote on 2010-03-27
Actually, it could recover on reboot, especially after running fsck (or e2fsck).  That would mark off the bad sectors, things would work okay, and then when  another sector goes, you get messages to run fsck on boot again.  If it is a failing drive, that would happen oftener and oftener until one day the whole thing conked.

If you go to System > Admin > Disk Utility, there's a whole bunch of tools to do disk checks.  I haven't had to use it yet myself, but I believe it can do various hardware checks that might at least allow you to exclude hardware issues.

---

### Post by dash86no on 2010-03-27
> **McButt said:**
> hey all, 
I've been having some weird hard drive failures on my mythtv/torrent computer, running a normal 9.10 ubuntu install. Hopefully someone here can tell me what's going on with this thing. The error seems to occur after the thing has been on for at least 1-2 days. The most recent occurrence didn't do any damage and was fixed by a reboot (and turning off the power supply for a moment), but other times I've had to run fsck to restore the data.
This is the syslog from the point where it goes wrong.
```
Mar 25 20:28:00 mythbox kernel: [143896.968589] ata1: lost interrupt (Status 0x50)
Mar 25 20:28:00 mythbox kernel: [143896.968619] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar 25 20:28:00 mythbox kernel: [143896.968635] ata1.00: cmd c8/00:28:98:d0:0a/00:00:00:00:00/e3 tag 0 dma 20480 in
Mar 25 20:28:00 mythbox kernel: [143896.968638]          res 40/00:00:00:4f:c2/00:00:00:00:00/10 Emask 0x4 (timeout)
Mar 25 20:28:00 mythbox kernel: [143896.968643] ata1.00: status: { DRDY }
Mar 25 20:28:00 mythbox kernel: [143896.968676] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143897.141186] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.141196] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.157046] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143897.189005] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143897.189016] ata1.00: device reported invalid CHS sector 0
Mar 25 20:28:00 mythbox kernel: [143897.189028] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143897.595158] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143897.595166] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143897.595180] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143897.595183]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143897.595188] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143897.595192] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143897.595225] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143897.765194] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.765204] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143897.781087] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143897.822273] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143897.822293] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143897.893650] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143897.893657] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143897.893670] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143897.893673]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143897.893678] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143897.893682] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143897.893715] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.065244] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.065254] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.081304] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.121085] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143898.121105] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.192136] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.192144] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.192157] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.192159]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.192165] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.192169] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.192201] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.361507] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.361517] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.377147] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.424776] ata1.01: configured for UDMA/100
Mar 25 20:28:00 mythbox kernel: [143898.424797] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.490623] ata1.01: limiting speed to UDMA/66:PIO4
Mar 25 20:28:00 mythbox kernel: [143898.490632] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.490638] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.490651] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.490654]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.490659] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.490663] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.490696] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.661741] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.661751] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.677165] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143898.717136] ata1.01: configured for UDMA/66
Mar 25 20:28:00 mythbox kernel: [143898.717156] ata1: EH complete
Mar 25 20:28:00 mythbox kernel: [143898.780812] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:28:00 mythbox kernel: [143898.780820] ata1.01: BMDMA stat 0x64
Mar 25 20:28:00 mythbox kernel: [143898.780833] ata1.01: cmd 35/00:08:87:02:e8/00:00:11:00:00/f0 tag 0 dma 4096 out
Mar 25 20:28:00 mythbox kernel: [143898.780835]          res 51/84:01:8e:02:e8/84:00:11:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:28:00 mythbox kernel: [143898.780841] ata1.01: status: { DRDY ERR }
Mar 25 20:28:00 mythbox kernel: [143898.780844] ata1.01: error: { ICRC ABRT }
Mar 25 20:28:00 mythbox kernel: [143898.780877] ata1: soft resetting link
Mar 25 20:28:00 mythbox kernel: [143898.953284] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.953293] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:28:00 mythbox kernel: [143898.969228] ata1.00: configured for UDMA/133
Mar 25 20:28:00 mythbox kernel: [143899.009471] ata1.01: configured for UDMA/66
Mar 25 20:28:00 mythbox kernel: [143899.009492] ata1: EH complete
Mar 25 20:30:01 mythbox CRON[15058]: (piet) CMD (/usr/local/bin/flexget     #Leest rss feed van torrent tracker en voegt gewenste torrents toe aan deluge)
Mar 25 20:30:01 mythbox CRON[15060]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:30:10 mythbox kernel: [144029.518076] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:30:10 mythbox kernel: [144029.518085] ata1.01: BMDMA stat 0x64
Mar 25 20:30:10 mythbox kernel: [144029.518098] ata1.01: cmd c8/00:60:e7:5e:59/00:00:00:00:00/f4 tag 0 dma 49152 in
Mar 25 20:30:10 mythbox kernel: [144029.518101]          res 51/84:00:46:5f:59/84:00:11:00:00/f4 Emask 0x10 (ATA bus error)
Mar 25 20:30:10 mythbox kernel: [144029.518156] ata1.01: status: { DRDY ERR }
Mar 25 20:30:10 mythbox kernel: [144029.518172] ata1.01: error: { ICRC ABRT }
Mar 25 20:30:10 mythbox kernel: [144029.518206] ata1: soft resetting link
Mar 25 20:30:11 mythbox kernel: [144029.689089] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:30:11 mythbox kernel: [144029.689098] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:30:11 mythbox kernel: [144029.705607] ata1.00: configured for UDMA/133
Mar 25 20:30:11 mythbox kernel: [144029.736953] ata1.01: configured for UDMA/66
Mar 25 20:30:11 mythbox kernel: [144029.736973] ata1: EH complete
Mar 25 20:30:17 mythbox sensord: Chip: it8712-isa-0290
Mar 25 20:30:17 mythbox sensord: Adapter: ISA adapter
Mar 25 20:30:17 mythbox sensord:   VCore 1: +1.30 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   VCore 2: +1.50 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   +3.3V: +3.07 V (min = +0.00 V, max = +4.08 V)
Mar 25 20:30:17 mythbox sensord:   +5V: +5.00 V (min = +0.00 V, max = +6.85 V)
Mar 25 20:30:17 mythbox sensord:   +12V: +11.97 V (min = +0.00 V, max = +16.32 V)
Mar 25 20:30:17 mythbox sensord:   -12V: -20.12 V (min = -27.36 V, max = +3.93 V)
Mar 25 20:30:17 mythbox sensord:   -5V: -6.30 V (min = -13.64 V, max = +4.03 V)
Mar 25 20:30:17 mythbox sensord:   Stdby: +4.95 V (min = +0.00 V, max = +6.85 V)
Mar 25 20:30:17 mythbox sensord:   VBat: +4.08 V
Mar 25 20:30:17 mythbox sensord:   fan1: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   fan2: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   fan3: 0 RPM (min = 0 RPM, div = 8)
Mar 25 20:30:17 mythbox sensord:   M/B Temp: 33.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   CPU Temp: 37.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   Temp3: 34.0 C (min = -1.0 C, max = 127.0 C)
Mar 25 20:30:17 mythbox sensord:   cpu0_vid: +0.000 V
Mar 25 20:31:15 mythbox kernel: [144094.204595] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:31:15 mythbox kernel: [144094.204604] ata1.01: BMDMA stat 0x64
Mar 25 20:31:15 mythbox kernel: [144094.204617] ata1.01: cmd 25/00:00:f7:d5:91/00:02:0d:00:00/f0 tag 0 dma 262144 in
Mar 25 20:31:15 mythbox kernel: [144094.204619]          res 51/84:00:f6:d7:91/84:00:0d:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:31:15 mythbox kernel: [144094.204625] ata1.01: status: { DRDY ERR }
Mar 25 20:31:15 mythbox kernel: [144094.204629] ata1.01: error: { ICRC ABRT }
Mar 25 20:31:15 mythbox kernel: [144094.204661] ata1: soft resetting link
Mar 25 20:31:15 mythbox kernel: [144094.374921] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:15 mythbox kernel: [144094.374931] ata1: nv_mode_filter: 0x1f39f&0x3f3ff->0x1f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:15 mythbox kernel: [144094.390821] ata1.00: configured for UDMA/133
Mar 25 20:31:15 mythbox kernel: [144094.430457] ata1.01: configured for UDMA/66
Mar 25 20:31:15 mythbox kernel: [144094.430477] ata1: EH complete
Mar 25 20:31:15 mythbox kernel: [144094.453279] ata1.01: limiting speed to UDMA/33:PIO4
Mar 25 20:31:15 mythbox kernel: [144094.453289] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Mar 25 20:31:15 mythbox kernel: [144094.453295] ata1.01: BMDMA stat 0x64
Mar 25 20:31:15 mythbox kernel: [144094.453308] ata1.01: cmd 25/00:00:f7:d5:91/00:02:0d:00:00/f0 tag 0 dma 262144 in
Mar 25 20:31:15 mythbox kernel: [144094.453311]          res 51/84:00:f6:d7:91/84:00:0d:00:00/f0 Emask 0x10 (ATA bus error)
Mar 25 20:31:15 mythbox kernel: [144094.453316] ata1.01: status: { DRDY ERR }
Mar 25 20:31:15 mythbox kernel: [144094.453320] ata1.01: error: { ICRC ABRT }
Mar 25 20:31:15 mythbox kernel: [144094.453353] ata1: soft resetting link
Mar 25 20:31:16 mythbox kernel: [144094.623273] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:16 mythbox kernel: [144094.623283] ata1: nv_mode_filter: 0x739f&0x3f3ff->0x739f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:16 mythbox kernel: [144094.640297] ata1.00: configured for UDMA/133
Mar 25 20:31:16 mythbox kernel: [144094.678644] ata1.01: model number mismatch 'SAMSUNG SP2014N' != 'CAMSENG CP"0!4N'
Mar 25 20:31:16 mythbox kernel: [144094.678651] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:16 mythbox kernel: [144094.678662] ata1.01: limiting speed to UDMA/33:PIO3
Mar 25 20:31:21 mythbox kernel: [144099.606874] ata1: soft resetting link
Mar 25 20:31:21 mythbox kernel: [144099.771192] ata1.01: model number mismatch 'SAMSUNG SP2014N' != 'SAMSENG CP"0!4N'
Mar 25 20:31:21 mythbox kernel: [144099.771199] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:21 mythbox kernel: [144099.771206] ata1.01: disabled
Mar 25 20:31:26 mythbox kernel: [144104.763343] ata1: soft resetting link
Mar 25 20:31:27 mythbox kernel: [144105.535942] ata1.01: ATA-7: SAMSUNG CP"014N, VC100-$1, max UDMA/100
Mar 25 20:31:27 mythbox kernel: [144105.535949] ata1.01: 390721968 sectors, multi 16: LBA48 
Mar 25 20:31:27 mythbox kernel: [144105.535985] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:27 mythbox kernel: [144105.535993] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:27 mythbox kernel: [144105.551965] ata1.00: configured for UDMA/133
Mar 25 20:31:27 mythbox kernel: [144105.583624] ata1.01: model number mismatch 'SAMSUNG CP"014N' != 'SAMSUNG SP2014N'
Mar 25 20:31:27 mythbox kernel: [144105.583632] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:27 mythbox kernel: [144105.583643] ata1.01: limiting speed to UDMA/100:PIO3
Mar 25 20:31:31 mythbox kernel: [144109.919802] ata1: soft resetting link
Mar 25 20:31:31 mythbox kernel: [144110.084114] ata1.01: model number mismatch 'SAMSUNG CP"014N' != 'SAMSUNG SP2014N'
Mar 25 20:31:31 mythbox kernel: [144110.084121] ata1.01: revalidation failed (errno=-19)
Mar 25 20:31:31 mythbox kernel: [144110.084128] ata1.01: disabled
Mar 25 20:31:31 mythbox kernel: [144110.092333] ata1: nv_mode_filter: 0x7f39f&0x7f3ff->0x7f39f, BIOS=0x7f000 (0xc7c6c000) ACPI=0x0
Mar 25 20:31:31 mythbox kernel: [144110.108624] ata1.00: configured for UDMA/133
Mar 25 20:31:31 mythbox kernel: [144110.108653] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 25 20:31:31 mythbox kernel: [144110.108660] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Mar 25 20:31:31 mythbox kernel: [144110.108667] Descriptor sense data with sense descriptors (in hex):
Mar 25 20:31:31 mythbox kernel: [144110.108671]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 25 20:31:31 mythbox kernel: [144110.108683]         0d 91 d7 f6 
Mar 25 20:31:31 mythbox kernel: [144110.108689] sd 0:0:1:0: [sdb] Add. Sense: Scsi parity error
Mar 25 20:31:31 mythbox kernel: [144110.108699] end_request: I/O error, dev sdb, sector 227661303
Mar 25 20:31:31 mythbox kernel: [144110.108738] ata1: EH complete
Mar 25 20:31:31 mythbox kernel: [144110.108900] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.161346] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.161388] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162096] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162126] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162305] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162324] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162339] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162621] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162674] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162693] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.162708] sd 0:0:1:0: rejecting I/O to offline device
Mar 25 20:31:31 mythbox kernel: [144110.257078] ata1.01: detaching (SCSI 0:0:1:0)
Mar 25 20:31:32 mythbox kernel: [144110.624546] sd 0:0:1:0: [sdb] Synchronizing SCSI cache
Mar 25 20:31:32 mythbox kernel: [144110.628991] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 25 20:31:32 mythbox kernel: [144110.629002] sd 0:0:1:0: [sdb] Stopping disk
Mar 25 20:31:32 mythbox kernel: [144110.629018] sd 0:0:1:0: [sdb] START_STOP FAILED
Mar 25 20:31:32 mythbox kernel: [144110.629022] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 25 20:31:32 mythbox kernel: [144110.962185] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144110.962200] Aborting journal on device sdb1.
Mar 25 20:31:32 mythbox kernel: [144110.962218] Remounting filesystem read-only
Mar 25 20:31:32 mythbox kernel: [144111.097743] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.097864] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.097965] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098062] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098157] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.098252] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9135075 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.101238] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102070] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102506] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102627] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.102725] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.104982] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.105466] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134929 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.240492] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.241258] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267593] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267768] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.267869] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.268835] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269074] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269275] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269381] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269477] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269575] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269671] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269766] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269862] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.269956] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270052] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270146] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270242] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270339] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270434] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270529] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270623] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270718] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270813] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.270908] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271003] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271098] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271193] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271288] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271383] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271477] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271572] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271667] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.271762] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278089] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278543] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.278873] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279337] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279590] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.279850] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.280000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.280339] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.282401] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.282794] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283046] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283287] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283526] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283763] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.283917] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284026] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284124] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284221] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284316] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284412] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284508] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284604] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284699] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284795] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.284890] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.285013] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.288897] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289254] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289561] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.289809] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290049] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290313] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290527] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290767] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290895] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.290999] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291095] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291189] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291283] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291377] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291471] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291565] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291660] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291753] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291847] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.291974] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292256] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292377] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292474] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292570] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292665] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292760] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292854] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.292949] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293062] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293157] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293253] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293348] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293443] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293537] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293632] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.293727] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.301148] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.301463] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9388033 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.302479] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.303632] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304022] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304364] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304617] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.304854] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305118] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305361] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305568] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305700] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305810] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.305910] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306024] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306122] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306219] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306316] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306481] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:32 mythbox kernel: [144111.306577] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9142587 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.309418] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362064] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362319] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362419] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:31:37 mythbox kernel: [144116.362515] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9642161 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.713871] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.760781] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.760940] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761042] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761210] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761326] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761424] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761523] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761622] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761720] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761817] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.761915] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762028] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762125] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762223] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762320] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762417] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762514] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:32:11 mythbox kernel: [144149.762610] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #9134927 offset 0
Mar 25 20:35:01 mythbox CRON[15136]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:38:14 mythbox kernel: [144512.991085] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.018880] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.019175] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:14 mythbox kernel: [144513.019435] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:38:49 mythbox kernel: [144547.549345] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
Mar 25 20:39:01 mythbox CRON[15196]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 25 20:40:01 mythbox CRON[15208]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Mar 25 20:40:01 mythbox CRON[15214]: (piet) CMD (/usr/local/bin/flexget     #Leest rss feed van torrent tracker en voegt gewenste torrents toe aan deluge)
Mar 25 20:43:07 mythbox kernel: [144805.761193] ext3_abort called.
Mar 25 20:43:07 mythbox kernel: [144805.761202] EXT3-fs error (device sdb1): ext3_put_super: Couldn't clean up the journal
```
Apparently the controller loses connection to the two hard drives and fails to restore it to one of them. This time it was the drive that only contains data, but I suspect it's been happening to the system drive as well because I've had two mysterious system crashes this month.
I don't think the drives are faulty, since they've always worked well in my main computer before being handed down to this one. Also if the drive fails you wouldn't expect it to be recovered on reboot, right?
Any ideas on what's going on here?

I just did some HDD troubleshooting myself, and would recommend gsmartcontrol GUI or smartctl from the command line.

---

### Post by McButt on 2010-03-27
> **quixote said:**
> Actually, it could recover on reboot, especially after running fsck (or e2fsck).  That would mark off the bad sectors, things would work okay, and then when  another sector goes, you get messages to run fsck on boot again.  If it is a failing drive, that would happen oftener and oftener until one day the whole thing conked.

If you go to System > Admin > Disk Utility, there's a whole bunch of tools to do disk checks.  I haven't had to use it yet myself, but I believe it can do various hardware checks that might at least allow you to exclude hardware issues.
I checked the disk utility tool (palimpsest) from the system menu. It reports both drives are okay, although it has relocated 4 bad sectors on sda (not the drive that failed in my opening post).
I'm gonna run some extended test on both drives now also with gsmartcontrol, maybe that reveals something.

---

### Post by McButt on 2010-03-28
I've run the tests in disk utility (palimpsest) and gsmartcontrol on both drives and both passed. It does label quite a lot as 'old age' and 'pre fail', but it still passes so I don't think that could be causing these problems. I've included the output of gsmartcontrol, perhaps someone will find something in there that stands out.

---

