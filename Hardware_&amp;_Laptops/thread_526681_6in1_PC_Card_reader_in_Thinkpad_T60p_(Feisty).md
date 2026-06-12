---
title: "6in1 PC Card reader in Thinkpad T60p (Feisty)"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Alexander Heß on 2007-08-15
I recently bought a [SanDisk 6-in-1 PC Card Adapter](http://www.sandisk.com/Products/Item(1140)-SDAD-67-A10-SanDisk_6in1_PC_Card_Adapter.aspx) since my T60p doesn't have an internal one.

When I insert the adapter with a SD card in the PCMCIA slot, the following appears in /var/log/syslog:

```

[ 9185.492000] pccard: PCMCIA card inserted into slot 0
[ 9185.492000] pcmcia: registering new device pcmcia0.0
[ 9185.532000] ata14: PATA max PIO0 cmd 0x0001a100 ctl 0x0001a10e bmdma 0x00000000 irq 3
[ 9185.532000] scsi16 : pata_pcmcia
[ 9185.708000] ATA: abnormal status 0x58 on port 0x0001a107
[ 9185.708000] ata14.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 9186.388000] ATA: abnormal status 0x58 on port 0x0001a107
[ 9186.388000] ata14.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 9186.388000] ata14.01: limiting speed to UDMA7:PIO5
[ 9187.068000] ATA: abnormal status 0x58 on port 0x0001a107
[ 9187.068000] ata14.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 9217.736000] ata14.00: qc timeout (cmd 0x91)
[ 9217.736000] ata14.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[ 9248.404000] ata14.00: qc timeout (cmd 0x91)
[ 9248.404000] ata14.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[ 9248.404000] ata14.00: limiting speed to UDMA7:PIO5
[ 9279.072000] ata14.00: qc timeout (cmd 0x91)
[ 9279.072000] ata14.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[1187039497.507517] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1').

```

When I boot from a Feisty Live CD, the SD card is mounted and the following appears in /var/log/syslog:

```

[ 5420.668000] pccard: PCMCIA card inserted into slot 0
[ 5420.668000] pcmcia: registering new device pcmcia0.0
[ 5420.708000] ata8: PATA max PIO0 cmd 0x0001a100 ctl 0x0001a10e bmdma 0x00000000 irq 4
[ 5420.708000] scsi7 : pata_pcmcia
[ 5420.884000] ATA: abnormal status 0x58 on port 0x0001a107
[ 5420.884000] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 5421.564000] ATA: abnormal status 0x58 on port 0x0001a107
[ 5421.564000] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 5421.564000] ata8.01: limiting speed to UDMA7:PIO5
[ 5422.244000] ATA: abnormal status 0x58 on port 0x0001a107
[ 5422.244000] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 5422.920000] ata8.00: CFA: Memory Card Adapter II, S2-V1.14, max PIO2
[ 5422.920000] ata8.00: 1984000 sectors, multi 0: LBA 
[ 5422.928000] ata8.00: configured for PIO0
[ 5422.928000] scsi 7:0:0:0: Direct-Access     ATA      Memory Card Adap S2-V PQ: 0 ANSI: 5
[ 5422.928000] SCSI device sdb: 1984000 512-byte hdwr sectors (1016 MB)
[ 5422.928000] sdb: Write Protect is off
[ 5422.928000] sdb: Mode Sense: 00 3a 00 00
[ 5422.928000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 5422.928000] SCSI device sdb: 1984000 512-byte hdwr sectors (1016 MB)
[ 5422.928000] sdb: Write Protect is off
[ 5422.928000] sdb: Mode Sense: 00 3a 00 00
[ 5422.928000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 5422.928000]  sdb: sdb1
[ 5422.932000] sd 7:0:0:0: Attached scsi removable disk sdb
[ 5422.932000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[1187086206.114726] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
[1187086206.146523] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_scsi_host'). 
[1187086206.153517] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_scsi_host_scsi_device_lun0'). 
[1187086206.155794] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_scsi_host_scsi_device_lun0_scsi_generic'). 
[1187086206.185758] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Memory_Card_Adapter_II'). 
[1187086206.391619] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4E32_6475').

```

It also works using a Dapper Live CD.

I already tried running the 2.6.20-15 kernel instead of 2.6.20-16 which didn't help. I also tried 2.6.22-9 using the guide I found here, which didn't help either.

**pccardctl ident** output:

```

Socket 0:
  product info: "             ", "Memory Card Adapter II", "V1.00", ""
  manfid: 0x0045, 0x0401
  function: 4 (fixed disk)

```

Tell me if you need more information…

---

