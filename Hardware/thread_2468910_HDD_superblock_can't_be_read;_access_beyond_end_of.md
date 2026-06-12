---
title: "HDD superblock can't be read; access beyond end of device"
date: 2021-11-14
forum: Hardware
---

### Post by knoeperkalle on 2021-11-14
Hi there,
Ubuntu newbie here :) I got 2 used SAS-drives for my old HP Z820 workstation and 1 just works fine (put it in, got recognized, formated it in the GUI-overview where you see your drives and mounted it there). The other one gets recognized after a few minutes but it doesn't show the size of the drive. Just the name and serial number is shown and you can't do anything with it. 
dmesg shows:  
> [COLOR=#111432][FONT=Arial][604088.963939] sd 9:0:4:0: [sde] Spinning up disk...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604089.970375] ..................................................................................................not responding...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.296970] sd 9:0:4:0: [sde] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.296976] sd 9:0:4:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.296979] sd 9:0:4:0: [sde] Add. Sense: Logical unit not ready, power cycle required[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.297125] sd 9:0:4:0: [sde] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.297128] sd 9:0:4:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.297130] sd 9:0:4:0: [sde] Add. Sense: Logical unit not ready, power cycle required[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.316837] sd 9:0:4:0: [sde] tag#1739 access beyond end of device[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.316850] blk_update_request: I/O error, dev sde, sector 2 op 0x0:(READ) flags 0x1000 phys_seg 1 prio class 0[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604189.316867] EXT4-fs (sde): unable to read superblock[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604756.037710] sd 9:0:4:0: device_block, handle(0x000c)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604757.787302] sd 9:0:4:0: device_unblock and setting to running, handle(0x000c)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604757.856905] mpt2sas_cm0: mpt3sas_transport_port_remove: removed: sas_addr(0x5000c500c9e0c63d)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604757.856917] mpt2sas_cm0: removing handle(0x000c), sas_addr(0x5000c500c9e0c63d)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604757.856922] mpt2sas_cm0: enclosure logical id(0x5001438025e29db1), slot(3)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.290956] scsi 9:0:5:0: Direct-Access [/FONT][/COLOR][COLOR=#111432][FONT=Arial]    [/FONT][/COLOR][COLOR=#111432][FONT=Arial]SEAGATE  ST10000NM0096[/FONT][/COLOR][COLOR=#111432][FONT=Arial]    [/FONT][/COLOR][COLOR=#111432][FONT=Arial]E005 PQ: 0 ANSI: 6[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.290968] scsi 9:0:5:0: SSP: handle(0x000c), sas_addr(0x5000c500c9e0c63d), phy(3), device_name(0x5000c500c9e0c63c)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.290971] scsi 9:0:5:0: enclosure logical id (0x5001438025e29db1), slot(3)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.290974] scsi 9:0:5:0: qdepth(254), tagged(1), scsi_level(7), cmd_que(1)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.298123] sd 9:0:5:0: Attached scsi generic sg4 type 0[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.300306]  end_device-9:5: add: handle(0x000c), sas_addr(0x5000c500c9e0c63d)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604954.302343] sd 9:0:5:0: [sde] Spinning up disk...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][604955.336340] ..................................................................................................not responding...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.660757] sd 9:0:5:0: [sde] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.660763] sd 9:0:5:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.660767] sd 9:0:5:0: [sde] Add. Sense: Logical unit is in process of becoming ready[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.663808] sd 9:0:5:0: [sde] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.663814] sd 9:0:5:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.663816] sd 9:0:5:0: [sde] Add. Sense: Logical unit is in process of becoming ready[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.669298] sd 9:0:5:0: [sde] 0 512-byte logical blocks: (0 B/0 B)[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.669302] sd 9:0:5:0: [sde] 0-byte physical blocks[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.672365] sd 9:0:5:0: [sde] Test WP failed, assume Write Enabled[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.673376] sd 9:0:5:0: [sde] Asking for cache data failed[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.673382] sd 9:0:5:0: [sde] Assuming drive cache: write through[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605054.740956] sd 9:0:5:0: [sde] Spinning up disk...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605055.782636] ..................................................................................................not responding...[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.107349] sd 9:0:5:0: [sde] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.107355] sd 9:0:5:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.107358] sd 9:0:5:0: [sde] Add. Sense: Logical unit is in process of becoming ready[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.110389] sd 9:0:5:0: [sde] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.110393] sd 9:0:5:0: [sde] Sense Key : Not Ready [current] [descriptor][/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.110395] sd 9:0:5:0: [sde] Add. Sense: Logical unit is in process of becoming ready[/FONT][/COLOR]
[COLOR=#111432][FONT=Arial][605155.124122] sd 9:0:5:0: [sde] Attached SCSI disk[/FONT][/COLOR]


fsck /dev/sde says that it can't read the superblock and suggest to use > sudo e2fsck -b 8193 /dev/sde or > sudo e2fsck -b 32768 /dev/sde if it is an ext2/ext3/ext4-drive. As I bought the drives used I don't know what they are but both variants just posted the same error with the superblock is not readable.

Any ideas? There are no data on the drives so no need to worry about data or backup :)

---

