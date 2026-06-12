---
title: "Broken hard drive?"
date: 2020-10-22
forum: Hardware
---

### Post by myrdrahl on 2020-10-22
I'm having issues with doing upgrades with apt, and after doing some prodding, i ran dmesg and get these errors. Is there any way to make the system disregard these sectors that are broken or do I have to bite the bullet here?


```

[   95.392059] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   95.394530] ata1.00: BMDMA stat 0x24
[   95.396932] ata1.00: failed command: READ DMA
[   95.399349] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[   95.403986] ata1.00: status: { DRDY ERR }
[   95.406279] ata1.00: error: { UNC }
[   95.572414] ata1.00: configured for UDMA/133
[   95.572427] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   95.572431] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[   95.572435] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[   95.572439] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[   95.572441] print_req_error: I/O error, dev sda, sector 230762140
[   95.574723] ata1: EH complete
[   95.574725] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[   98.576069] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   98.578399] ata1.00: BMDMA stat 0x24
[   98.580658] ata1.00: failed command: READ DMA
[   98.582873] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[   98.587223] ata1.00: status: { DRDY ERR }
[   98.589354] ata1.00: error: { UNC }
[   98.898587] ata1.00: configured for UDMA/133
[   98.898601] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   98.898605] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[   98.898609] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[   98.898613] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[   98.898615] print_req_error: I/O error, dev sda, sector 230762140
[   98.900673] ata1: EH complete
[   98.900720] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[  316.384323] EXT4-fs (sda2): error count since last fsck: 1238
[  316.384373] EXT4-fs (sda2): initial error at time 1554357790: ext4_find_entry:1436: inode 7209462
[  316.384386] EXT4-fs (sda2): last error at time 1603346202: ext4_find_entry:1455: inode 7209462
[  791.404034] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  791.404077] ata1.00: BMDMA stat 0x24
[  791.404098] ata1.00: failed command: READ DMA
[  791.404122] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  791.404189] ata1.00: status: { DRDY ERR }
[  791.404210] ata1.00: error: { UNC }
[  791.572464] ata1.00: configured for UDMA/133
[  791.572477] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  791.572482] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  791.572485] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  791.572490] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  791.572493] print_req_error: I/O error, dev sda, sector 230762140
[  791.572567] ata1: EH complete
[  791.572580] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[  794.452050] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  794.452103] ata1.00: BMDMA stat 0x24
[  794.452133] ata1.00: failed command: READ DMA
[  794.452167] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  794.452237] ata1.00: status: { DRDY ERR }
[  794.452263] ata1.00: error: { UNC }
[  794.655082] ata1.00: configured for UDMA/133
[  794.655093] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  794.655096] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  794.655099] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  794.655103] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  794.655105] print_req_error: I/O error, dev sda, sector 230762140
[  794.655172] ata1: EH complete
[  794.655190] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[  917.128053] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  917.128092] ata1.00: BMDMA stat 0x24
[  917.128114] ata1.00: failed command: READ DMA
[  917.128140] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  917.128210] ata1.00: status: { DRDY ERR }
[  917.128232] ata1.00: error: { UNC }
[  917.296615] ata1.00: configured for UDMA/133
[  917.296628] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  917.296632] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  917.296636] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  917.296640] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  917.296643] print_req_error: I/O error, dev sda, sector 230762140
[  917.296717] ata1: EH complete
[  917.296730] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[  920.252069] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  920.252125] ata1.00: BMDMA stat 0x24
[  920.252156] ata1.00: failed command: READ DMA
[  920.252194] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  920.252272] ata1.00: status: { DRDY ERR }
[  920.252292] ata1.00: error: { UNC }
[  920.587103] ata1.00: configured for UDMA/133
[  920.587114] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  920.587117] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  920.587121] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  920.587125] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  920.587127] print_req_error: I/O error, dev sda, sector 230762140
[  920.587193] ata1: EH complete
[  920.587212] EXT4-fs error (device sda2): ext4_find_entry:1455: inode #7209462: comm dpkg: reading directory lblock 0
[  951.128108] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  951.128165] ata1.00: BMDMA stat 0x24
[  951.128196] ata1.00: failed command: READ DMA
[  951.128238] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  951.128304] ata1.00: status: { DRDY ERR }
[  951.128325] ata1.00: error: { UNC }
[  951.292231] ata1.00: configured for UDMA/133
[  951.292247] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  951.292251] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  951.292254] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  951.292258] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  951.292261] print_req_error: I/O error, dev sda, sector 230762140
[  951.292344] ata1: EH complete
[  951.292353] EXT4-fs warning (device sda2): htree_dirblock_to_tree:994: inode #7209462: lblock 0: comm ls: error -5 reading directory block
[  957.484109] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  957.484165] ata1.00: BMDMA stat 0x24
[  957.484195] ata1.00: failed command: READ DMA
[  957.485596] ata1.00: cmd c8/00:08:98:26:c1/00:00:00:00:00/ed tag 0 dma 4096 in
                        res 51/40:00:9c:26:c1/00:00:00:00:00/0d Emask 0x9 (media error)
[  957.488437] ata1.00: status: { DRDY ERR }
[  957.489914] ata1.00: error: { UNC }
[  957.639270] ata1.00: configured for UDMA/133
[  957.639286] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  957.639289] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current]
[  957.639293] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  957.639297] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 0d c1 26 98 00 00 08 00
[  957.639300] print_req_error: I/O error, dev sda, sector 230762140

```

---

### Post by ActionParsnip on 2020-10-22
I'd say it was failing. New SSDs are pretty cheap. Run a last full backup if possible ASAP

---

### Post by myrdrahl on 2020-10-22
Thanks! That's what I was afraid of, I'll have a try with cloning the drive.

---

### Post by slickymaster on 2020-10-22
*Thread moved to **Hardware**.*

---

