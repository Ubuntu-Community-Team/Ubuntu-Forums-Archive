---
title: "Can't mount coolmax HD-360 enclosure"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by ivotron on 2007-06-30
Hi,

I've just bought a [coolmax HD-360 enclosure]("http://www.coolmaxusa.com/productDetails.asp?item=HD-360&details=features&subcategory=U2&category=3.5") to use it with my 200 GB WD2000 hard disk but Ubuntu (Xubuntu) can't mount it. The message on dmesg:

```
Jun 30 15:01:09 ivotron-desktop kernel: [  740.673885] usb 4-6: USB disconnect, address 6
Jun 30 15:03:01 ivotron-desktop kernel: [  852.978830] usb 4-6: new high speed USB device using ehci_hcd and address 7
Jun 30 15:03:02 ivotron-desktop kernel: [  853.111742] usb 4-6: configuration #1 chosen from 1 choice
Jun 30 15:03:02 ivotron-desktop kernel: [  853.112039] scsi5 : SCSI emulation for USB Mass Storage devices
Jun 30 15:03:07 ivotron-desktop kernel: [  858.108102]   Vendor: WDC WD20  Model: 00JB-00DUA0       Rev:  0 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.108115]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun 30 15:03:07 ivotron-desktop kernel: [  858.110069] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
Jun 30 15:03:07 ivotron-desktop kernel: [  858.110692] sda: Write Protect is off
Jun 30 15:03:07 ivotron-desktop kernel: [  858.111568] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
Jun 30 15:03:07 ivotron-desktop kernel: [  858.112189] sda: Write Protect is off
Jun 30 15:03:07 ivotron-desktop kernel: [  858.112199]  sda:<6>sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.135055] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.135061] printk: 122 messages suppressed.
Jun 30 15:03:07 ivotron-desktop kernel: [  858.139672] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.139679] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.139705]  unable to read partition table
Jun 30 15:03:07 ivotron-desktop kernel: [  858.139802] sd 5:0:0:0: Attached scsi disk sda
Jun 30 15:03:07 ivotron-desktop kernel: [  858.139852] sd 5:0:0:0: Attached scsi generic sg0 type 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.205859] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.205865] end_request: I/O error, dev sda, sector 390721792
Jun 30 15:03:07 ivotron-desktop kernel: [  858.209975] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.209980] end_request: I/O error, dev sda, sector 390721792
Jun 30 15:03:07 ivotron-desktop kernel: [  858.219318] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.219324] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.223466] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.223470] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.228070] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.228076] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.232206] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.232210] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.237213] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.237220] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.241449] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.241453] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.245568] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.245572] end_request: I/O error, dev sda, sector 390721904
Jun 30 15:03:07 ivotron-desktop kernel: [  858.249440] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.249445] end_request: I/O error, dev sda, sector 390721904
Jun 30 15:03:07 ivotron-desktop kernel: [  858.253436] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.253440] end_request: I/O error, dev sda, sector 390721952
Jun 30 15:03:07 ivotron-desktop kernel: [  858.257434] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.257440] end_request: I/O error, dev sda, sector 390721952
Jun 30 15:03:07 ivotron-desktop kernel: [  858.261561] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.261568] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.265550] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.265554] end_request: I/O error, dev sda, sector 390721960
Jun 30 15:03:07 ivotron-desktop kernel: [  858.269421] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.269425] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.274056] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.274063] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.278039] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.278043] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.284173] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.284180] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.289404] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.289408] end_request: I/O error, dev sda, sector 8
Jun 30 15:03:07 ivotron-desktop kernel: [  858.293899] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.293902] end_request: I/O error, dev sda, sector 16
Jun 30 15:03:07 ivotron-desktop kernel: [  858.298284] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.298290] end_request: I/O error, dev sda, sector 24
Jun 30 15:03:07 ivotron-desktop kernel: [  858.301518] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.301521] end_request: I/O error, dev sda, sector 32
Jun 30 15:03:07 ivotron-desktop kernel: [  858.304765] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.304769] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.309520] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.309527] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.313509] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.313512] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.333528] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.333536] end_request: I/O error, dev sda, sector 40
Jun 30 15:03:07 ivotron-desktop kernel: [  858.352853] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.352857] end_request: I/O error, dev sda, sector 48
Jun 30 15:03:07 ivotron-desktop kernel: [  858.371603] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.371610] end_request: I/O error, dev sda, sector 56
Jun 30 15:03:07 ivotron-desktop kernel: [  858.389827] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.389833] end_request: I/O error, dev sda, sector 64
Jun 30 15:03:07 ivotron-desktop kernel: [  858.407069] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.407076] end_request: I/O error, dev sda, sector 72
Jun 30 15:03:07 ivotron-desktop kernel: [  858.424549] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.424556] end_request: I/O error, dev sda, sector 80
Jun 30 15:03:07 ivotron-desktop kernel: [  858.442658] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.442665] end_request: I/O error, dev sda, sector 88
Jun 30 15:03:07 ivotron-desktop kernel: [  858.458391] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.458397] end_request: I/O error, dev sda, sector 96
Jun 30 15:03:07 ivotron-desktop kernel: [  858.474381] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.474388] end_request: I/O error, dev sda, sector 104
Jun 30 15:03:07 ivotron-desktop kernel: [  858.488931] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.488938] end_request: I/O error, dev sda, sector 112
Jun 30 15:03:07 ivotron-desktop kernel: [  858.502475] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.502482] end_request: I/O error, dev sda, sector 120
Jun 30 15:03:07 ivotron-desktop kernel: [  858.515834] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.515840] end_request: I/O error, dev sda, sector 128
Jun 30 15:03:07 ivotron-desktop kernel: [  858.528711] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.528718] end_request: I/O error, dev sda, sector 136
Jun 30 15:03:07 ivotron-desktop kernel: [  858.540689] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.540695] end_request: I/O error, dev sda, sector 144
Jun 30 15:03:07 ivotron-desktop kernel: [  858.551930] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.551936] end_request: I/O error, dev sda, sector 152
Jun 30 15:03:07 ivotron-desktop kernel: [  858.562427] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.562433] end_request: I/O error, dev sda, sector 160
Jun 30 15:03:07 ivotron-desktop kernel: [  858.572166] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.572173] end_request: I/O error, dev sda, sector 168
Jun 30 15:03:07 ivotron-desktop kernel: [  858.581898] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.581902] end_request: I/O error, dev sda, sector 176
Jun 30 15:03:07 ivotron-desktop kernel: [  858.596270] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.596277] end_request: I/O error, dev sda, sector 184
Jun 30 15:03:07 ivotron-desktop kernel: [  858.607095] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.607102] end_request: I/O error, dev sda, sector 192
Jun 30 15:03:07 ivotron-desktop kernel: [  858.631087] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.631110] end_request: I/O error, dev sda, sector 200
Jun 30 15:03:07 ivotron-desktop kernel: [  858.655059] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.655077] end_request: I/O error, dev sda, sector 208
Jun 30 15:03:07 ivotron-desktop kernel: [  858.671947] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.671953] end_request: I/O error, dev sda, sector 216
Jun 30 15:03:07 ivotron-desktop kernel: [  858.677809] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.677812] end_request: I/O error, dev sda, sector 224
Jun 30 15:03:07 ivotron-desktop kernel: [  858.683565] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.683571] end_request: I/O error, dev sda, sector 232
Jun 30 15:03:07 ivotron-desktop kernel: [  858.688051] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.688055] end_request: I/O error, dev sda, sector 240
Jun 30 15:03:07 ivotron-desktop kernel: [  858.691926] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.691933] end_request: I/O error, dev sda, sector 248
Jun 30 15:03:07 ivotron-desktop kernel: [  858.695542] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.695545] end_request: I/O error, dev sda, sector 256
Jun 30 15:03:07 ivotron-desktop kernel: [  858.699650] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.699654] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.703286] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.703291] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.706982] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.706985] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.710776] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.710779] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.714524] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.714529] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.719033] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.719040] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.722894] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.722900] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.726138] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.726141] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.729639] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.729644] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.733261] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.733265] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.737130] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.737135] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.741258] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.741264] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.745122] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.745126] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.748743] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.748746] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.753626] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.753633] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.757611] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.757616] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.760857] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.760860] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.764612] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.764618] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.768102] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.768106] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.771477] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.771483] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.783843] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.783849] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.788217] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.788224] end_request: I/O error, dev sda, sector 8
Jun 30 15:03:07 ivotron-desktop kernel: [  858.791955] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.791958] end_request: I/O error, dev sda, sector 16
Jun 30 15:03:07 ivotron-desktop kernel: [  858.795326] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.795329] end_request: I/O error, dev sda, sector 24
Jun 30 15:03:07 ivotron-desktop kernel: [  858.798950] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.798953] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.803095] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.803100] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.812235] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.812242] end_request: I/O error, dev sda, sector 32
Jun 30 15:03:07 ivotron-desktop kernel: [  858.819208] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.819212] end_request: I/O error, dev sda, sector 40
Jun 30 15:03:07 ivotron-desktop kernel: [  858.825556] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.825562] end_request: I/O error, dev sda, sector 48
Jun 30 15:03:07 ivotron-desktop kernel: [  858.831546] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.831550] end_request: I/O error, dev sda, sector 56
Jun 30 15:03:07 ivotron-desktop kernel: [  858.837048] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.837056] end_request: I/O error, dev sda, sector 64
Jun 30 15:03:07 ivotron-desktop kernel: [  858.841536] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.841540] end_request: I/O error, dev sda, sector 72
Jun 30 15:03:07 ivotron-desktop kernel: [  858.845156] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.845160] end_request: I/O error, dev sda, sector 80
Jun 30 15:03:07 ivotron-desktop kernel: [  858.849041] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.849048] end_request: I/O error, dev sda, sector 88
Jun 30 15:03:07 ivotron-desktop kernel: [  858.852401] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.852404] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.856773] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.856777] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.860775] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.860782] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.864889] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.864893] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  858.880895] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.880901] end_request: I/O error, dev sda, sector 96
Jun 30 15:03:07 ivotron-desktop kernel: [  858.895750] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.895757] end_request: I/O error, dev sda, sector 104
Jun 30 15:03:07 ivotron-desktop kernel: [  858.911121] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.911128] end_request: I/O error, dev sda, sector 112
Jun 30 15:03:07 ivotron-desktop kernel: [  858.924603] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.924609] end_request: I/O error, dev sda, sector 120
Jun 30 15:03:07 ivotron-desktop kernel: [  858.938089] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.938096] end_request: I/O error, dev sda, sector 128
Jun 30 15:03:07 ivotron-desktop kernel: [  858.950857] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.950864] end_request: I/O error, dev sda, sector 136
Jun 30 15:03:07 ivotron-desktop kernel: [  858.962689] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.962696] end_request: I/O error, dev sda, sector 144
Jun 30 15:03:07 ivotron-desktop kernel: [  858.973936] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.973943] end_request: I/O error, dev sda, sector 152
Jun 30 15:03:07 ivotron-desktop kernel: [  858.984421] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.984428] end_request: I/O error, dev sda, sector 160
Jun 30 15:03:07 ivotron-desktop kernel: [  858.994154] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  858.994158] end_request: I/O error, dev sda, sector 168
Jun 30 15:03:07 ivotron-desktop kernel: [  859.004121] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.004127] end_request: I/O error, dev sda, sector 176
Jun 30 15:03:07 ivotron-desktop kernel: [  859.013135] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.013138] end_request: I/O error, dev sda, sector 184
Jun 30 15:03:07 ivotron-desktop kernel: [  859.021252] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.021256] end_request: I/O error, dev sda, sector 192
Jun 30 15:03:07 ivotron-desktop kernel: [  859.028755] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.028761] end_request: I/O error, dev sda, sector 200
Jun 30 15:03:07 ivotron-desktop kernel: [  859.035748] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.035755] end_request: I/O error, dev sda, sector 208
Jun 30 15:03:07 ivotron-desktop kernel: [  859.043120] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.043126] end_request: I/O error, dev sda, sector 216
Jun 30 15:03:07 ivotron-desktop kernel: [  859.049102] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.049106] end_request: I/O error, dev sda, sector 224
Jun 30 15:03:07 ivotron-desktop kernel: [  859.054229] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.054235] end_request: I/O error, dev sda, sector 232
Jun 30 15:03:07 ivotron-desktop kernel: [  859.058717] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.058720] end_request: I/O error, dev sda, sector 240
Jun 30 15:03:07 ivotron-desktop kernel: [  859.062338] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.062341] end_request: I/O error, dev sda, sector 248
Jun 30 15:03:07 ivotron-desktop kernel: [  859.067221] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.067228] end_request: I/O error, dev sda, sector 256
Jun 30 15:03:07 ivotron-desktop kernel: [  859.070957] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.070960] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  859.074830] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.074835] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  859.079082] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.079089] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  859.083070] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.083073] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  859.086819] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.086823] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:07 ivotron-desktop kernel: [  859.090563] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:07 ivotron-desktop kernel: [  859.090566] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.094309] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.094312] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.098056] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.098060] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.102192] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.102199] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.105675] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.105678] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.109423] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.109427] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.113170] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.113174] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.117291] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.117295] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.121160] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.121163] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.124786] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.124792] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.128780] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.128784] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.134412] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.134420] end_request: I/O error, dev sda, sector 0
Jun 30 15:03:08 ivotron-desktop kernel: [  859.138520] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 30 15:03:08 ivotron-desktop kernel: [  859.138525] end_request: I/O error, dev sda, sector 0

```

Windows recognizes the drive immediately and can read/write files from/to it (when formatted as NTFS). I can mount the drive fine if I attach it to the IDE interface. I've also tried by using another HDD (a 40 GB Hitachi) to test if the disk is broken but same thing happens (coolmax doesn't work, IDE does), so I guess that the problem is in the coolmax interface.

Lastly, I can read and write on other kind of usb devices (tested with a Kingston 1GB flash drive and I'm using a USB mouse).

System specs:

[LIST]
[*]IBM NetVista 8305
[*]BIOS Updated
[*]Xubuntu Edgy
[*]Linux 2.6.17.11-386
[/LIST]

I'd really appreciate your help here. 

Thanks.

---

