---
title: "Disappearing and reappearing drives in JBOD"
date: 2014-04-09
forum: Hardware
---

### Post by DeadlyDeadOne on 2014-04-09
Hi all.

I have a JBOD enclosure with a dozen SATA 2TB HDDs of various brands.  Individually they all work fine and pass SMART tests.  They're connected to an LSI HBA and an HP SAS Expander.  I'm running Ubntu 12.0.4 LTS, fully updated, with ZOL.

```
     Port Name         Chip Vendor/Type/Rev    MPT Rev  Firmware Rev  IOC
 1.  /proc/mpt/ioc0    LSI Logic SAS1068E B3     105      01210000     0
Current active firmware version is 01210000 (1.33.00)
Firmware image's version is MPTFW-01.33.00.00-IT
x86 BIOS image's version is MPTBIOS-6.36.00.00 (2011.08.24)
```

I want to add more drives, same types as what I already have.  Again, they've all been checked and confirmed to work fine and they pass SMART tests.
Adding a couple poses no problem.  I can add 2 and the system is stable for many hours.  When I add a 3rd or 4th, taking the total count up to 15 or 16, things go haywire and I start to see DID_NO_CONNECTs in the log and different drives randomly disappear then reappear.

```
Apr  9 23:50:43 UZFS kernel: [ 3213.521096] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 2, phy 2, sas_addr 0x500143800668fe82
Apr  9 23:50:43 UZFS kernel: [ 3213.528768] scsi 8:0:11:0: Direct-Access     ATA      WDC WD20EARS-00M AB50 PQ: 0 ANSI: 5
Apr  9 23:50:43 UZFS kernel: [ 3213.530670] sd 8:0:11:0: Attached scsi generic sg12 type 0
Apr  9 23:50:43 UZFS kernel: [ 3213.538211] sd 8:0:11:0: [sdl] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:50:43 UZFS kernel: [ 3213.565610] sd 8:0:11:0: [sdl] Write Protect is off
Apr  9 23:50:43 UZFS kernel: [ 3213.565616] sd 8:0:11:0: [sdl] Mode Sense: 73 00 00 08
Apr  9 23:50:43 UZFS kernel: [ 3213.573105] sd 8:0:11:0: [sdl] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:50:43 UZFS kernel: [ 3213.686397]  sdl:
Apr  9 23:50:43 UZFS kernel: [ 3213.748434] sd 8:0:11:0: [sdl] Attached SCSI disk
Apr  9 23:50:45 UZFS kernel: [ 3215.176869] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 10, phy 10, sas_addr 0x500143800668fe8a
Apr  9 23:50:45 UZFS kernel: [ 3215.190492] scsi 8:0:12:0: Direct-Access     ATA      SAMSUNG HD204UI  0001 PQ: 0 ANSI: 5
Apr  9 23:50:45 UZFS kernel: [ 3215.192389] sd 8:0:12:0: Attached scsi generic sg13 type 0
Apr  9 23:50:45 UZFS kernel: [ 3215.206177] sd 8:0:12:0: [sdm] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:50:45 UZFS kernel: [ 3215.233643] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:50:45 UZFS kernel: [ 3215.235923] scsi 8:0:13:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:50:45 UZFS kernel: [ 3215.237813] sd 8:0:13:0: Attached scsi generic sg14 type 0
Apr  9 23:50:45 UZFS kernel: [ 3215.240591] sd 8:0:13:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:50:45 UZFS kernel: [ 3215.311484] sd 8:0:13:0: [sdn] Write Protect is off
Apr  9 23:50:45 UZFS kernel: [ 3215.311490] sd 8:0:13:0: [sdn] Mode Sense: 73 00 00 08
Apr  9 23:50:45 UZFS kernel: [ 3215.314807] sd 8:0:13:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:50:45 UZFS kernel: [ 3215.434963]  sdn:
Apr  9 23:50:45 UZFS kernel: [ 3215.511869] sd 8:0:12:0: [sdm] Write Protect is off
Apr  9 23:50:45 UZFS kernel: [ 3215.511875] sd 8:0:12:0: [sdm] Mode Sense: 73 00 00 08
Apr  9 23:50:45 UZFS kernel: [ 3215.516031] sd 8:0:13:0: [sdn] Attached SCSI disk
Apr  9 23:50:45 UZFS kernel: [ 3215.525417] sd 8:0:12:0: [sdm] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:50:45 UZFS kernel: [ 3215.889379]  sdm:
Apr  9 23:50:46 UZFS kernel: [ 3216.245571] sd 8:0:12:0: [sdm] Attached SCSI disk
Apr  9 23:50:46 UZFS kernel: [ 3216.677608] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 6, phy 6, sas_addr 0x500143800668fe86
Apr  9 23:50:46 UZFS kernel: [ 3216.686445] scsi 8:0:14:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
Apr  9 23:50:46 UZFS kernel: [ 3216.688411] sd 8:0:14:0: Attached scsi generic sg15 type 0
Apr  9 23:50:46 UZFS kernel: [ 3216.697360] sd 8:0:14:0: [sdo] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:50:46 UZFS kernel: [ 3216.716052] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 19, phy 18, sas_addr 0x500143800668fe92
Apr  9 23:50:46 UZFS kernel: [ 3216.718221] scsi 8:0:15:0: Direct-Access     ATA      ST2000DM001-1CH1 CC43 PQ: 0 ANSI: 5
Apr  9 23:50:46 UZFS kernel: [ 3216.720342] sd 8:0:15:0: Attached scsi generic sg16 type 0
Apr  9 23:50:46 UZFS kernel: [ 3216.722772] sd 8:0:15:0: [sdp] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:50:46 UZFS kernel: [ 3216.728643] sd 8:0:15:0: [sdp] Write Protect is off
Apr  9 23:50:46 UZFS kernel: [ 3216.728647] sd 8:0:15:0: [sdp] Mode Sense: 73 00 00 08
Apr  9 23:50:46 UZFS kernel: [ 3216.730188] sd 8:0:14:0: [sdo] Write Protect is off
Apr  9 23:50:46 UZFS kernel: [ 3216.730191] sd 8:0:14:0: [sdo] Mode Sense: 73 00 00 08
Apr  9 23:50:46 UZFS kernel: [ 3216.731951] sd 8:0:15:0: [sdp] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:50:46 UZFS kernel: [ 3216.739457] sd 8:0:14:0: [sdo] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:50:46 UZFS kernel: [ 3216.803229]  sdp:
Apr  9 23:50:46 UZFS kernel: [ 3216.817850] sd 8:0:15:0: [sdp] Attached SCSI disk
Apr  9 23:50:46 UZFS kernel: [ 3216.840133]  sdo:
Apr  9 23:50:46 UZFS kernel: [ 3216.899149] sd 8:0:14:0: [sdo] Attached SCSI disk
Apr  9 23:51:14 UZFS kernel: [ 3244.385290]  end_device-8:0:14: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:51:14 UZFS kernel: [ 3244.385297]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:51:14 UZFS kernel: [ 3244.385305]  port-8:0:14: mptsas: ioc0: delete port 14, sas_addr (0x500143800668fe8e)
Apr  9 23:51:14 UZFS kernel: [ 3244.385921] sd 8:0:13:0: [sdn] Synchronizing SCSI cache
Apr  9 23:51:14 UZFS kernel: [ 3244.385996] sd 8:0:13:0: [sdn]  
Apr  9 23:51:14 UZFS kernel: [ 3244.386000] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:51:14 UZFS kernel: [ 3244.386069] scsi target8:0:13: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:51:22 UZFS kernel: [ 3252.752630] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:51:22 UZFS kernel: [ 3252.754900] scsi 8:0:16:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:51:22 UZFS kernel: [ 3252.756829] sd 8:0:16:0: Attached scsi generic sg14 type 0
Apr  9 23:51:22 UZFS kernel: [ 3252.759303] sd 8:0:16:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:51:22 UZFS kernel: [ 3252.830063] sd 8:0:16:0: [sdn] Write Protect is off
Apr  9 23:51:22 UZFS kernel: [ 3252.830068] sd 8:0:16:0: [sdn] Mode Sense: 73 00 00 08
Apr  9 23:51:22 UZFS kernel: [ 3252.833158] sd 8:0:16:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:51:23 UZFS kernel: [ 3252.953544]  sdn:
Apr  9 23:51:23 UZFS kernel: [ 3253.035415] sd 8:0:16:0: [sdn] Attached SCSI disk
Apr  9 23:51:36 UZFS kernel: [ 3266.863476]  end_device-8:0:17: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:51:36 UZFS kernel: [ 3266.863483]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:51:36 UZFS kernel: [ 3266.863492]  port-8:0:17: mptsas: ioc0: delete port 17, sas_addr (0x500143800668fe8e)
Apr  9 23:51:36 UZFS kernel: [ 3266.863958] sd 8:0:16:0: [sdn] Synchronizing SCSI cache
Apr  9 23:51:36 UZFS kernel: [ 3266.864022] sd 8:0:16:0: [sdn]  
Apr  9 23:51:36 UZFS kernel: [ 3266.864028] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:51:36 UZFS kernel: [ 3266.864095] scsi target8:0:16: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:51:44 UZFS kernel: [ 3273.969094] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:51:44 UZFS kernel: [ 3273.971342] scsi 8:0:17:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:51:44 UZFS kernel: [ 3273.973231] sd 8:0:17:0: Attached scsi generic sg14 type 0
Apr  9 23:51:44 UZFS kernel: [ 3273.975689] sd 8:0:17:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:51:44 UZFS kernel: [ 3274.046950] sd 8:0:17:0: [sdn] Write Protect is off
Apr  9 23:51:44 UZFS kernel: [ 3274.046956] sd 8:0:17:0: [sdn] Mode Sense: 73 00 00 08
Apr  9 23:51:44 UZFS kernel: [ 3274.050098] sd 8:0:17:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:51:44 UZFS kernel: [ 3274.170466]  sdn:
Apr  9 23:51:44 UZFS kernel: [ 3274.251408] sd 8:0:17:0: [sdn] Attached SCSI disk
Apr  9 23:53:17 UZFS kernel: [ 3367.582739] Fusion MPT misc device (ioctl) driver 3.04.20
Apr  9 23:53:17 UZFS kernel: [ 3367.582791] mptctl: Registered with Fusion MPT base driver
Apr  9 23:53:17 UZFS kernel: [ 3367.582794] mptctl: /dev/mptctl @ (major,minor=10,220)
Apr  9 23:54:21 UZFS kernel: [ 3431.071857] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 1, phy 1, sas_addr 0x500143800668fe81
Apr  9 23:54:21 UZFS kernel: [ 3431.078979] scsi 8:0:18:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
Apr  9 23:54:21 UZFS kernel: [ 3431.080956] sd 8:0:18:0: Attached scsi generic sg17 type 0
Apr  9 23:54:21 UZFS kernel: [ 3431.088166] sd 8:0:18:0: [sdq] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:54:21 UZFS kernel: [ 3431.115381] sd 8:0:18:0: [sdq] Write Protect is off
Apr  9 23:54:21 UZFS kernel: [ 3431.115388] sd 8:0:18:0: [sdq] Mode Sense: 73 00 00 08
Apr  9 23:54:21 UZFS kernel: [ 3431.121816] sd 8:0:18:0: [sdq] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:54:21 UZFS kernel: [ 3431.239154]  sdq:
Apr  9 23:54:21 UZFS kernel: [ 3431.289191] sd 8:0:18:0: [sdq] Attached SCSI disk
Apr  9 23:57:06 UZFS kernel: [ 3596.415816] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 5, phy 5, sas_addr 0x500143800668fe85
Apr  9 23:57:06 UZFS kernel: [ 3596.425383] scsi 8:0:19:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
Apr  9 23:57:06 UZFS kernel: [ 3596.427800] sd 8:0:19:0: Attached scsi generic sg18 type 0
Apr  9 23:57:06 UZFS kernel: [ 3596.432494] sd 8:0:19:0: [sdr] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:57:06 UZFS kernel: [ 3596.455687]  end_device-8:0:18: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:57:06 UZFS kernel: [ 3596.455693]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:57:06 UZFS kernel: [ 3596.455699]  port-8:0:18: mptsas: ioc0: delete port 18, sas_addr (0x500143800668fe8e)
Apr  9 23:57:06 UZFS kernel: [ 3596.470926] sd 8:0:19:0: [sdr] Write Protect is off
Apr  9 23:57:06 UZFS kernel: [ 3596.470933] sd 8:0:19:0: [sdr] Mode Sense: 73 00 00 08
Apr  9 23:57:06 UZFS kernel: [ 3596.479492] sd 8:0:19:0: [sdr] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:57:07 UZFS kernel: [ 3596.581820]  sdr:
Apr  9 23:57:07 UZFS kernel: [ 3596.656894] sd 8:0:19:0: [sdr] Attached SCSI disk
Apr  9 23:57:07 UZFS kernel: [ 3596.657275] sd 8:0:17:0: [sdn] Synchronizing SCSI cache
Apr  9 23:57:07 UZFS kernel: [ 3596.657327] sd 8:0:17:0: [sdn]  
Apr  9 23:57:07 UZFS kernel: [ 3596.657331] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:57:07 UZFS kernel: [ 3596.657427] scsi target8:0:17: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:57:14 UZFS kernel: [ 3604.164434] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:57:14 UZFS kernel: [ 3604.166698] scsi 8:0:20:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:57:14 UZFS kernel: [ 3604.168635] sd 8:0:20:0: Attached scsi generic sg14 type 0
Apr  9 23:57:14 UZFS kernel: [ 3604.171055] sd 8:0:20:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:57:14 UZFS kernel: [ 3604.239348] sd 8:0:20:0: [sdn] Write Protect is off
Apr  9 23:57:14 UZFS kernel: [ 3604.239362] sd 8:0:20:0: [sdn] Mode Sense: 73 00 00 08
Apr  9 23:57:14 UZFS kernel: [ 3604.242445] sd 8:0:20:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:57:14 UZFS kernel: [ 3604.362748]  sdn:
Apr  9 23:57:14 UZFS kernel: [ 3604.443757] sd 8:0:20:0: [sdn] Attached SCSI disk
Apr  9 23:58:09 UZFS kernel: [ 3659.234693]  end_device-8:0:5: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 4, phy 4,sas_addr 0x500143800668fe84
Apr  9 23:58:09 UZFS kernel: [ 3659.234700]  phy-8:0:12: mptsas: ioc0: delete phy 4, phy-obj (0xffff88020fbbc800)
Apr  9 23:58:09 UZFS kernel: [ 3659.234708]  port-8:0:5: mptsas: ioc0: delete port 5, sas_addr (0x500143800668fe84)
Apr  9 23:58:09 UZFS kernel: [ 3659.235856] sd 8:0:4:0: [sde] Synchronizing SCSI cache
Apr  9 23:58:09 UZFS kernel: [ 3659.235919] sd 8:0:4:0: [sde]  
Apr  9 23:58:09 UZFS kernel: [ 3659.235923] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:58:09 UZFS kernel: [ 3659.236026] scsi target8:0:4: mptsas: ioc0: delete device: fw_channel 0, fw_id 4, phy 4, sas_addr 0x500143800668fe84
Apr  9 23:58:09 UZFS kernel: [ 3659.236259]  end_device-8:0:11: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 20, phy 19,sas_addr 0x500143800668fe93
Apr  9 23:58:09 UZFS kernel: [ 3659.236265]  phy-8:0:27: mptsas: ioc0: delete phy 19, phy-obj (0xffff88021028f400)
Apr  9 23:58:09 UZFS kernel: [ 3659.236273]  port-8:0:11: mptsas: ioc0: delete port 11, sas_addr (0x500143800668fe93)
Apr  9 23:58:09 UZFS kernel: [ 3659.237105] sd 8:0:10:0: [sdk] Synchronizing SCSI cache
Apr  9 23:58:09 UZFS kernel: [ 3659.237159] sd 8:0:10:0: [sdk]  
Apr  9 23:58:09 UZFS kernel: [ 3659.237163] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:58:09 UZFS kernel: [ 3659.237257] scsi target8:0:10: mptsas: ioc0: delete device: fw_channel 0, fw_id 20, phy 19, sas_addr 0x500143800668fe93
Apr  9 23:58:09 UZFS kernel: [ 3659.237478]  end_device-8:0:21: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:58:09 UZFS kernel: [ 3659.237484]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:58:09 UZFS kernel: [ 3659.237492]  port-8:0:21: mptsas: ioc0: delete port 21, sas_addr (0x500143800668fe8e)
Apr  9 23:58:09 UZFS kernel: [ 3659.237887] sd 8:0:20:0: [sdn] Synchronizing SCSI cache
Apr  9 23:58:09 UZFS kernel: [ 3659.237940] sd 8:0:20:0: [sdn]  
Apr  9 23:58:09 UZFS kernel: [ 3659.237944] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:58:09 UZFS kernel: [ 3659.238031] scsi target8:0:20: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:58:15 UZFS kernel: [ 3664.835536] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:58:15 UZFS kernel: [ 3664.837788] scsi 8:0:21:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:58:15 UZFS kernel: [ 3664.839744] sd 8:0:21:0: Attached scsi generic sg5 type 0
Apr  9 23:58:15 UZFS kernel: [ 3664.842249] sd 8:0:21:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:58:15 UZFS kernel: [ 3664.910750] sd 8:0:21:0: [sde] Write Protect is off
Apr  9 23:58:15 UZFS kernel: [ 3664.910756] sd 8:0:21:0: [sde] Mode Sense: 73 00 00 08
Apr  9 23:58:15 UZFS kernel: [ 3664.913841] sd 8:0:21:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:58:15 UZFS kernel: [ 3665.034232]  sde:
Apr  9 23:58:15 UZFS kernel: [ 3665.115276] sd 8:0:21:0: [sde] Attached SCSI disk
Apr  9 23:58:18 UZFS kernel: [ 3667.733622] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 4, phy 4, sas_addr 0x500143800668fe84
Apr  9 23:58:18 UZFS kernel: [ 3667.743457] scsi 8:0:22:0: Direct-Access     ATA      WDC WD20EARS-00M AB51 PQ: 0 ANSI: 5
Apr  9 23:58:18 UZFS kernel: [ 3667.745493] sd 8:0:22:0: Attached scsi generic sg11 type 0
Apr  9 23:58:18 UZFS kernel: [ 3667.754737] sd 8:0:22:0: [sdk] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:58:18 UZFS kernel: [ 3667.774037] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 20, phy 19, sas_addr 0x500143800668fe93
Apr  9 23:58:18 UZFS kernel: [ 3667.776166] scsi 8:0:23:0: Direct-Access     ATA      ST2000DM001-9YN1 CC4C PQ: 0 ANSI: 5
Apr  9 23:58:18 UZFS kernel: [ 3667.778004] sd 8:0:23:0: Attached scsi generic sg14 type 0
Apr  9 23:58:18 UZFS kernel: [ 3667.780673] sd 8:0:23:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:58:18 UZFS kernel: [ 3667.788548] sd 8:0:22:0: [sdk] Write Protect is off
Apr  9 23:58:18 UZFS kernel: [ 3667.788554] sd 8:0:22:0: [sdk] Mode Sense: 73 00 00 08
Apr  9 23:58:18 UZFS kernel: [ 3667.797064] sd 8:0:22:0: [sdk] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:58:18 UZFS kernel: [ 3667.845852] sd 8:0:23:0: [sdn] Write Protect is off
Apr  9 23:58:18 UZFS kernel: [ 3667.845866] sd 8:0:23:0: [sdn] Mode Sense: 73 00 00 08
Apr  9 23:58:18 UZFS kernel: [ 3667.849179] sd 8:0:23:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:58:18 UZFS kernel: [ 3667.925525]  sdk:
Apr  9 23:58:18 UZFS kernel: [ 3667.987460] sd 8:0:22:0: [sdk] Attached SCSI disk
Apr  9 23:58:18 UZFS kernel: [ 3667.988074]  sdn:
Apr  9 23:58:18 UZFS kernel: [ 3668.059736] sd 8:0:23:0: [sdn] Attached SCSI disk
Apr  9 23:59:04 UZFS kernel: [ 3713.929617]  end_device-8:0:22: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:59:04 UZFS kernel: [ 3713.929624]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:59:04 UZFS kernel: [ 3713.929631]  port-8:0:22: mptsas: ioc0: delete port 22, sas_addr (0x500143800668fe8e)
Apr  9 23:59:04 UZFS kernel: [ 3713.930128] sd 8:0:21:0: [sde] Synchronizing SCSI cache
Apr  9 23:59:04 UZFS kernel: [ 3713.930191] sd 8:0:21:0: [sde]  
Apr  9 23:59:04 UZFS kernel: [ 3713.930196] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:59:04 UZFS kernel: [ 3713.930277] scsi target8:0:21: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:09 UZFS kernel: [ 3718.798379] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 9, phy 9, sas_addr 0x500143800668fe89
Apr  9 23:59:09 UZFS kernel: [ 3718.812025] scsi 8:0:24:0: Direct-Access     ATA      SAMSUNG HD204UI  0001 PQ: 0 ANSI: 5
Apr  9 23:59:09 UZFS kernel: [ 3718.813882] sd 8:0:24:0: Attached scsi generic sg5 type 0
Apr  9 23:59:09 UZFS kernel: [ 3718.827707] sd 8:0:24:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:59:09 UZFS kernel: [ 3719.134615] sd 8:0:24:0: [sde] Write Protect is off
Apr  9 23:59:09 UZFS kernel: [ 3719.134621] sd 8:0:24:0: [sde] Mode Sense: 73 00 00 08
Apr  9 23:59:09 UZFS kernel: [ 3719.147591] sd 8:0:24:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:59:10 UZFS kernel: [ 3719.512168]  sde:
Apr  9 23:59:10 UZFS kernel: [ 3720.037091] sd 8:0:24:0: [sde] Attached SCSI disk
Apr  9 23:59:10 UZFS kernel: [ 3720.055753] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:10 UZFS kernel: [ 3720.058082] scsi 8:0:25:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:59:10 UZFS kernel: [ 3720.060019] sd 8:0:25:0: Attached scsi generic sg19 type 0
Apr  9 23:59:10 UZFS kernel: [ 3720.062420] sd 8:0:25:0: [sds] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:59:10 UZFS kernel: [ 3720.134714] sd 8:0:25:0: [sds] Write Protect is off
Apr  9 23:59:10 UZFS kernel: [ 3720.134722] sd 8:0:25:0: [sds] Mode Sense: 73 00 00 08
Apr  9 23:59:10 UZFS kernel: [ 3720.138737] sd 8:0:25:0: [sds] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:59:10 UZFS kernel: [ 3720.258223]  sds:
Apr  9 23:59:10 UZFS kernel: [ 3720.339179] sd 8:0:25:0: [sds] Attached SCSI disk
Apr  9 23:59:12 UZFS kernel: [ 3722.421375]  end_device-8:0:26: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:59:12 UZFS kernel: [ 3722.421382]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:59:12 UZFS kernel: [ 3722.421390]  port-8:0:26: mptsas: ioc0: delete port 26, sas_addr (0x500143800668fe8e)
Apr  9 23:59:12 UZFS kernel: [ 3722.421910] sd 8:0:25:0: [sds] Synchronizing SCSI cache
Apr  9 23:59:12 UZFS kernel: [ 3722.421972] sd 8:0:25:0: [sds]  
Apr  9 23:59:12 UZFS kernel: [ 3722.421976] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:59:12 UZFS kernel: [ 3722.422082] scsi target8:0:25: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:19 UZFS kernel: [ 3729.281187] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:19 UZFS kernel: [ 3729.283402] scsi 8:0:26:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:59:19 UZFS kernel: [ 3729.285309] sd 8:0:26:0: Attached scsi generic sg19 type 0
Apr  9 23:59:19 UZFS kernel: [ 3729.287840] sd 8:0:26:0: [sds] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:59:19 UZFS kernel: [ 3729.361612] sd 8:0:26:0: [sds] Write Protect is off
Apr  9 23:59:19 UZFS kernel: [ 3729.361618] sd 8:0:26:0: [sds] Mode Sense: 73 00 00 08
Apr  9 23:59:19 UZFS kernel: [ 3729.364679] sd 8:0:26:0: [sds] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:59:20 UZFS kernel: [ 3729.485091]  sds:
Apr  9 23:59:20 UZFS kernel: [ 3729.566017] sd 8:0:26:0: [sds] Attached SCSI disk
Apr  9 23:59:22 UZFS kernel: [ 3731.912166]  end_device-8:0:27: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:59:22 UZFS kernel: [ 3731.912172]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:59:22 UZFS kernel: [ 3731.912180]  port-8:0:27: mptsas: ioc0: delete port 27, sas_addr (0x500143800668fe8e)
Apr  9 23:59:22 UZFS kernel: [ 3731.912774] sd 8:0:26:0: [sds] Synchronizing SCSI cache
Apr  9 23:59:22 UZFS kernel: [ 3731.912835] sd 8:0:26:0: [sds]  
Apr  9 23:59:22 UZFS kernel: [ 3731.912839] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:59:22 UZFS kernel: [ 3731.912935] scsi target8:0:26: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:29 UZFS kernel: [ 3738.522942] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr  9 23:59:29 UZFS kernel: [ 3738.525156] scsi 8:0:27:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr  9 23:59:29 UZFS kernel: [ 3738.527025] sd 8:0:27:0: Attached scsi generic sg19 type 0
Apr  9 23:59:29 UZFS kernel: [ 3738.529529] sd 8:0:27:0: [sds] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr  9 23:59:29 UZFS kernel: [ 3738.604794] sd 8:0:27:0: [sds] Write Protect is off
Apr  9 23:59:29 UZFS kernel: [ 3738.604799] sd 8:0:27:0: [sds] Mode Sense: 73 00 00 08
Apr  9 23:59:29 UZFS kernel: [ 3738.607914] sd 8:0:27:0: [sds] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 23:59:29 UZFS kernel: [ 3738.728214]  sds:
Apr  9 23:59:29 UZFS kernel: [ 3738.809162] sd 8:0:27:0: [sds] Attached SCSI disk
Apr  9 23:59:56 UZFS kernel: [ 3766.130958]  end_device-8:0:28: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr  9 23:59:56 UZFS kernel: [ 3766.130964]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr  9 23:59:56 UZFS kernel: [ 3766.130971]  port-8:0:28: mptsas: ioc0: delete port 28, sas_addr (0x500143800668fe8e)
Apr  9 23:59:56 UZFS kernel: [ 3766.131572] sd 8:0:27:0: [sds] Synchronizing SCSI cache
Apr  9 23:59:56 UZFS kernel: [ 3766.131634] sd 8:0:27:0: [sds]  
Apr  9 23:59:56 UZFS kernel: [ 3766.131639] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  9 23:59:56 UZFS kernel: [ 3766.131739] scsi target8:0:27: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr 10 00:00:02 UZFS kernel: [ 3771.988249] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr 10 00:00:02 UZFS kernel: [ 3771.990502] scsi 8:0:28:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr 10 00:00:02 UZFS kernel: [ 3771.992378] sd 8:0:28:0: Attached scsi generic sg19 type 0
Apr 10 00:00:02 UZFS kernel: [ 3771.994887] sd 8:0:28:0: [sds] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 10 00:00:02 UZFS kernel: [ 3772.062539] sd 8:0:28:0: [sds] Write Protect is off
Apr 10 00:00:02 UZFS kernel: [ 3772.062545] sd 8:0:28:0: [sds] Mode Sense: 73 00 00 08
Apr 10 00:00:02 UZFS kernel: [ 3772.065653] sd 8:0:28:0: [sds] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 10 00:00:02 UZFS kernel: [ 3772.186002]  sds:
Apr 10 00:00:02 UZFS kernel: [ 3772.266988] sd 8:0:28:0: [sds] Attached SCSI disk
Apr 10 00:00:06 UZFS kernel: [ 3776.121263]  end_device-8:0:29: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 14, phy 14,sas_addr 0x500143800668fe8e
Apr 10 00:00:06 UZFS kernel: [ 3776.121270]  phy-8:0:22: mptsas: ioc0: delete phy 14, phy-obj (0xffff88021028e000)
Apr 10 00:00:06 UZFS kernel: [ 3776.121278]  port-8:0:29: mptsas: ioc0: delete port 29, sas_addr (0x500143800668fe8e)
Apr 10 00:00:06 UZFS kernel: [ 3776.121855] sd 8:0:28:0: [sds] Synchronizing SCSI cache
Apr 10 00:00:06 UZFS kernel: [ 3776.121914] sd 8:0:28:0: [sds]  
Apr 10 00:00:06 UZFS kernel: [ 3776.121919] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 10 00:00:06 UZFS kernel: [ 3776.122014] scsi target8:0:28: mptsas: ioc0: delete device: fw_channel 0, fw_id 14, phy 14, sas_addr 0x500143800668fe8e
Apr 10 00:00:10 UZFS kernel: [ 3779.865628]  end_device-8:0:6: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 17, phy 16,sas_addr 0x500143800668fe90
Apr 10 00:00:10 UZFS kernel: [ 3779.865634]  phy-8:0:24: mptsas: ioc0: delete phy 16, phy-obj (0xffff88021028f800)
Apr 10 00:00:10 UZFS kernel: [ 3779.865642]  port-8:0:6: mptsas: ioc0: delete port 6, sas_addr (0x500143800668fe90)
Apr 10 00:00:10 UZFS kernel: [ 3779.866128] sd 8:0:5:0: [sdf] Synchronizing SCSI cache
Apr 10 00:00:10 UZFS kernel: [ 3779.866192] sd 8:0:5:0: [sdf]  
Apr 10 00:00:10 UZFS kernel: [ 3779.866197] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 10 00:00:10 UZFS kernel: [ 3779.866267] scsi target8:0:5: mptsas: ioc0: delete device: fw_channel 0, fw_id 17, phy 16, sas_addr 0x500143800668fe90
Apr 10 00:00:11 UZFS kernel: [ 3781.360178]  end_device-8:0:24: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 20, phy 19,sas_addr 0x500143800668fe93
Apr 10 00:00:11 UZFS kernel: [ 3781.360185]  phy-8:0:27: mptsas: ioc0: delete phy 19, phy-obj (0xffff88021028f400)
Apr 10 00:00:11 UZFS kernel: [ 3781.360193]  port-8:0:24: mptsas: ioc0: delete port 24, sas_addr (0x500143800668fe93)
Apr 10 00:00:11 UZFS kernel: [ 3781.360599] sd 8:0:23:0: [sdn] Synchronizing SCSI cache
Apr 10 00:00:11 UZFS kernel: [ 3781.360635] sd 8:0:23:0: [sdn]  
Apr 10 00:00:11 UZFS kernel: [ 3781.360638] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 10 00:00:11 UZFS kernel: [ 3781.360678] scsi target8:0:23: mptsas: ioc0: delete device: fw_channel 0, fw_id 20, phy 19, sas_addr 0x500143800668fe93
Apr 10 00:00:17 UZFS kernel: [ 3787.136097] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 13, phy 13, sas_addr 0x500143800668fe8d
Apr 10 00:00:17 UZFS kernel: [ 3787.138440] scsi 8:0:29:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr 10 00:00:17 UZFS kernel: [ 3787.140425] sd 8:0:29:0: Attached scsi generic sg6 type 0
Apr 10 00:00:17 UZFS kernel: [ 3787.142876] sd 8:0:29:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 10 00:00:17 UZFS kernel: [ 3787.214466] sd 8:0:29:0: [sdf] Write Protect is off
Apr 10 00:00:17 UZFS kernel: [ 3787.214471] sd 8:0:29:0: [sdf] Mode Sense: 73 00 00 08
Apr 10 00:00:17 UZFS kernel: [ 3787.217912] sd 8:0:29:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 10 00:00:17 UZFS kernel: [ 3787.218604] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 17, phy 16, sas_addr 0x500143800668fe90
Apr 10 00:00:17 UZFS kernel: [ 3787.222166] scsi 8:0:30:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
Apr 10 00:00:17 UZFS kernel: [ 3787.224689] sd 8:0:30:0: Attached scsi generic sg14 type 0
Apr 10 00:00:17 UZFS kernel: [ 3787.228088] sd 8:0:30:0: [sdn] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 10 00:00:17 UZFS kernel: [ 3787.300201] sd 8:0:30:0: [sdn] Write Protect is off
Apr 10 00:00:17 UZFS kernel: [ 3787.300206] sd 8:0:30:0: [sdn] Mode Sense: 73 00 00 08
Apr 10 00:00:17 UZFS kernel: [ 3787.303297] sd 8:0:30:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 10 00:00:17 UZFS kernel: [ 3787.330907]  sdf:
Apr 10 00:00:18 UZFS kernel: [ 3787.411542] sd 8:0:29:0: [sdf] Attached SCSI disk
Apr 10 00:00:18 UZFS kernel: [ 3787.415849]  sdn:
Apr 10 00:00:18 UZFS kernel: [ 3787.497259] sd 8:0:30:0: [sdn] Attached SCSI disk
```

Powering up the machine with all drives in place produces a different result....

```
Apr 10 02:03:09 UZFS dbus[1267]: [system] Successfully activated service 'org.freedesktop.UDisks'
Apr 10 02:03:25 UZFS kernel: [   93.991866] audit_printk_skb: 138 callbacks suppressed
Apr 10 02:03:25 UZFS kernel: [   93.991869] type=1400 audit(1397059405.080:70): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2396 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr 10 02:03:26 UZFS goa[2401]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Apr 10 02:03:32 UZFS udevd[598]: timeout '/sbin/blkid -o udev -p /dev/sdm'
Apr 10 02:03:32 UZFS udevd[819]: timeout '/sbin/blkid -o udev -p /dev/sde'
Apr 10 02:03:32 UZFS udevd[750]: timeout 'udisks-part-id /dev/sdk'
Apr 10 02:03:32 UZFS udevd[638]: timeout: killing '/sbin/modprobe -bv scsi:t-0x0d' [904]
Apr 10 02:03:32 UZFS udevd[667]: timeout '/sbin/blkid -o udev -p /dev/sdn'
Apr 10 02:03:32 UZFS udevd[814]: timeout '/sbin/blkid -o udev -p /dev/sdl'
Apr 10 02:03:33 UZFS udevd[598]: timeout: killing '/sbin/blkid -o udev -p /dev/sdm' [940]
Apr 10 02:03:33 UZFS udevd[819]: timeout: killing '/sbin/blkid -o udev -p /dev/sde' [942]
Apr 10 02:03:33 UZFS udevd[750]: timeout: killing 'udisks-part-id /dev/sdk' [955]
Apr 10 02:03:33 UZFS udevd[819]: '/sbin/blkid -o udev -p /dev/sde' [942] terminated by signal 9 (Killed)
Apr 10 02:03:33 UZFS udevd[819]: timeout '/lib/udev/vdev_id -d sde'
Apr 10 02:03:33 UZFS udevd[819]: timeout 'udisks-part-id /dev/sde'
Apr 10 02:03:33 UZFS udevd[638]: timeout: killing '/sbin/modprobe -bv scsi:t-0x0d' [904]
Apr 10 02:03:33 UZFS udevd[667]: timeout: killing '/sbin/blkid -o udev -p /dev/sdn' [938]
Apr 10 02:03:33 UZFS udevd[814]: timeout: killing '/sbin/blkid -o udev -p /dev/sdl' [943]
Apr 10 02:03:34 UZFS udevd[598]: timeout: killing '/sbin/blkid -o udev -p /dev/sdm' [940]
Apr 10 02:03:34 UZFS udevd[750]: timeout: killing 'udisks-part-id /dev/sdk' [955]
Apr 10 02:03:34 UZFS udevd[819]: timeout: killing 'udisks-part-id /dev/sde' [2559]
Apr 10 02:03:34 UZFS udevd[638]: timeout: killing '/sbin/modprobe -bv scsi:t-0x0d' [904]
Apr 10 02:03:34 UZFS udevd[667]: timeout: killing '/sbin/blkid -o udev -p /dev/sdn' [938]
Apr 10 02:03:34 UZFS udevd[814]: timeout: killing '/sbin/blkid -o udev -p /dev/sdl' [943]
Apr 10 02:03:35 UZFS udevd[598]: timeout: killing '/sbin/blkid -o udev -p /dev/sdm' [940]
Apr 10 02:03:35 UZFS udevd[750]: timeout: killing 'udisks-part-id /dev/sdk' [955]
Apr 10 02:03:35 UZFS udevd[819]: timeout: killing 'udisks-part-id /dev/sde' [2559]
....
```

... repeating ad-infinitum over random disks.

I've tried all manner of combinations of the Seagate, WD and Samsung disks.  I've tried different motherboard slots for controllers and expanders.
I've tried all drives on the SAS Expander, 4 drives on the LSI and the rest on the Expander, and also tried 4 drives on the LSI with 8 drives on an Adaptec RAID controller and the others on the Expander.  All of the above produce the same result of drives disappearing and reappearing once the total number is 15 or greater.
I've tried disabling SMART in /lib/udev/rules.d (after reading about possible passthrough issues to SATA drives with SAS). Didn't help.

The same hardware configuration works with OpenIndiana but I want to use Ubuntu.

What should I try next?

---

