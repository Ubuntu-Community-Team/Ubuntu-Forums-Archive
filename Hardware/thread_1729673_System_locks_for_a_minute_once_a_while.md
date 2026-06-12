---
title: "System locks for a minute once a while"
date: 2011-04-15
forum: Hardware
---

### Post by asalockout on 2011-04-15
System takes time to respond with what ever its doing when this** happens its a new hdd. 
System keeps on reading or writing from hdd for almost one minute until it stops, i havent seen fsck running at boot.
Kubuntu 10.10 Kde 4.6.2    kernel 2.6.35-28-generic


**
Laptop    kernel    [  493.138791] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138802] ata3.00: BMDMA stat 0x24
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138811] ata3.00: failed command: READ DMA
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138829] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138833]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138841] ata3.00: status: { DRDY ERR }
04/14/11 12:18:56 PM    Laptop    kernel    [  493.138847] ata3.00: error: { UNC }
04/14/11 12:18:56 PM    Laptop    kernel    [  493.328936] ata3.00: configured for UDMA/133
04/14/11 12:18:56 PM    Laptop    kernel    [  493.328960] ata3: EH complete
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790729] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790740] ata3.00: BMDMA stat 0x24
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790749] ata3.00: failed command: READ DMA
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790767] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790770]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790779] ata3.00: status: { DRDY ERR }
04/14/11 12:18:59 PM    Laptop    kernel    [  495.790785] ata3.00: error: { UNC }
04/14/11 12:18:59 PM    Laptop    kernel    [  495.952996] ata3.00: configured for UDMA/133
04/14/11 12:18:59 PM    Laptop    kernel    [  495.953020] ata3: EH complete
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443880] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443890] ata3.00: BMDMA stat 0x24
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443899] ata3.00: failed command: READ DMA
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443917] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443920]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443929] ata3.00: status: { DRDY ERR }
04/14/11 12:19:02 PM    Laptop    kernel    [  498.443935] ata3.00: error: { UNC }
04/14/11 12:19:02 PM    Laptop    kernel    [  498.584987] ata3.00: configured for UDMA/133
04/14/11 12:19:02 PM    Laptop    kernel    [  498.585008] ata3: EH complete
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954194] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954203] ata3.00: BMDMA stat 0x24
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954211] ata3.00: failed command: READ DMA
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954229] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954233]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954241] ata3.00: status: { DRDY ERR }
04/14/11 12:19:04 PM    Laptop    kernel    [  500.954247] ata3.00: error: { UNC }
04/14/11 12:19:04 PM    Laptop    kernel    [  501.116972] ata3.00: configured for UDMA/133
04/14/11 12:19:04 PM    Laptop    kernel    [  501.116989] ata3: EH complete
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475535] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475544] ata3.00: BMDMA stat 0x24
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475552] ata3.00: failed command: READ DMA
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475570] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475574]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475582] ata3.00: status: { DRDY ERR }
04/14/11 12:19:07 PM    Laptop    kernel    [  503.475588] ata3.00: error: { UNC }
04/14/11 12:19:07 PM    Laptop    kernel    [  503.636828] ata3.00: configured for UDMA/133
04/14/11 12:19:07 PM    Laptop    kernel    [  503.636846] ata3: EH complete
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018866] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018875] ata3.00: BMDMA stat 0x24
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018883] ata3.00: failed command: READ DMA
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018900] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018904]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018912] ata3.00: status: { DRDY ERR }
04/14/11 12:19:09 PM    Laptop    kernel    [  506.018918] ata3.00: error: { UNC }
04/14/11 12:19:09 PM    Laptop    kernel    [  506.160978] ata3.00: configured for UDMA/133
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161002] sd 2:0:0:0: [sda] Unhandled sense code
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161008] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161017] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161028] Descriptor sense data with sense descriptors (in hex):
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161034]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161058]         00 24 28 0e 
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161068] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161082] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 24 28 08 00 00 08 00
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161105] end_request: I/O error, dev sda, sector 2369550
04/14/11 12:19:09 PM    Laptop    kernel    [  506.161132] ata3: EH complete
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661438] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661448] ata3.00: BMDMA stat 0x24
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661457] ata3.00: failed command: READ DMA
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661475] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661479]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661487] ata3.00: status: { DRDY ERR }
04/14/11 12:19:12 PM    Laptop    kernel    [  508.661493] ata3.00: error: { UNC }
04/14/11 12:19:12 PM    Laptop    kernel    [  508.856851] ata3.00: configured for UDMA/133
04/14/11 12:19:12 PM    Laptop    kernel    [  508.856871] ata3: EH complete
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314661] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314671] ata3.00: BMDMA stat 0x24
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314679] ata3.00: failed command: READ DMA
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314697] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314701]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314709] ata3.00: status: { DRDY ERR }
04/14/11 12:19:14 PM    Laptop    kernel    [  511.314715] ata3.00: error: { UNC }
04/14/11 12:19:15 PM    Laptop    kernel    [  511.476985] ata3.00: configured for UDMA/133
04/14/11 12:19:15 PM    Laptop    kernel    [  511.477003] ata3: EH complete
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858005] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858014] ata3.00: BMDMA stat 0x24
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858023] ata3.00: failed command: READ DMA
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858040] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858044]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858052] ata3.00: status: { DRDY ERR }
04/14/11 12:19:17 PM    Laptop    kernel    [  513.858058] ata3.00: error: { UNC }
04/14/11 12:19:17 PM    Laptop    kernel    [  514.020839] ata3.00: configured for UDMA/133
04/14/11 12:19:17 PM    Laptop    kernel    [  514.020857] ata3: EH complete
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412542] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412552] ata3.00: BMDMA stat 0x24
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412561] ata3.00: failed command: READ DMA
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412579] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412582]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412591] ata3.00: status: { DRDY ERR }
04/14/11 12:19:20 PM    Laptop    kernel    [  516.412597] ata3.00: error: { UNC }
04/14/11 12:19:20 PM    Laptop    kernel    [  516.564918] ata3.00: configured for UDMA/133
04/14/11 12:19:20 PM    Laptop    kernel    [  516.564938] ata3: EH complete
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088046] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088057] ata3.00: BMDMA stat 0x24
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088066] ata3.00: failed command: READ DMA
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088084] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088087]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088096] ata3.00: status: { DRDY ERR }
04/14/11 12:19:22 PM    Laptop    kernel    [  519.088102] ata3.00: error: { UNC }
04/14/11 12:19:22 PM    Laptop    kernel    [  519.240878] ata3.00: configured for UDMA/133
04/14/11 12:19:22 PM    Laptop    kernel    [  519.240902] ata3: EH complete
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598314] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598325] ata3.00: BMDMA stat 0x24
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598334] ata3.00: failed command: READ DMA
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598352] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598356]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598364] ata3.00: status: { DRDY ERR }
04/14/11 12:19:25 PM    Laptop    kernel    [  521.598370] ata3.00: error: { UNC }
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760924] ata3.00: configured for UDMA/133
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760953] sd 2:0:0:0: [sda] Unhandled sense code
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760959] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760968] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760980] Descriptor sense data with sense descriptors (in hex):
04/14/11 12:19:25 PM    Laptop    kernel    [  521.760985]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/14/11 12:19:25 PM    Laptop    kernel    [  521.761010]         00 24 28 0e 
04/14/11 12:19:25 PM    Laptop    kernel    [  521.761020] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
04/14/11 12:19:25 PM    Laptop    kernel    [  521.761034] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 24 28 08 00 00 08 00
04/14/11 12:19:25 PM    Laptop    kernel    [  521.761056] end_request: I/O error, dev sda, sector 2369550
04/14/11 12:19:25 PM    Laptop    kernel    [  521.761089] ata3: EH complete
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185661] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185672] ata3.00: BMDMA stat 0x24
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185681] ata3.00: failed command: READ DMA
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185699] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185703]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185711] ata3.00: status: { DRDY ERR }
04/14/11 12:19:27 PM    Laptop    kernel    [  524.185717] ata3.00: error: { UNC }
04/14/11 12:19:28 PM    Laptop    kernel    [  524.436981] ata3.00: configured for UDMA/133
04/14/11 12:19:28 PM    Laptop    kernel    [  524.437003] ata3: EH complete
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828170] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828179] ata3.00: BMDMA stat 0x24
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828187] ata3.00: failed command: READ DMA
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828205] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828209]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828217] ata3.00: status: { DRDY ERR }
04/14/11 12:19:30 PM    Laptop    kernel    [  526.828223] ata3.00: error: { UNC }
04/14/11 12:19:30 PM    Laptop    kernel    [  526.980959] ata3.00: configured for UDMA/133
04/14/11 12:19:30 PM    Laptop    kernel    [  526.980974] ata3: EH complete
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470510] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470519] ata3.00: BMDMA stat 0x24
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470527] ata3.00: failed command: READ DMA
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470544] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470548]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470556] ata3.00: status: { DRDY ERR }
04/14/11 12:19:33 PM    Laptop    kernel    [  529.470562] ata3.00: error: { UNC }
04/14/11 12:19:33 PM    Laptop    kernel    [  529.609001] ata3.00: configured for UDMA/133
04/14/11 12:19:33 PM    Laptop    kernel    [  529.609017] ata3: EH complete
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035914] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035922] ata3.00: BMDMA stat 0x24
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035930] ata3.00: failed command: READ DMA
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035948] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035952]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035959] ata3.00: status: { DRDY ERR }
04/14/11 12:19:35 PM    Laptop    kernel    [  532.035965] ata3.00: error: { UNC }
04/14/11 12:19:35 PM    Laptop    kernel    [  532.238039] ata3.00: configured for UDMA/133
04/14/11 12:19:35 PM    Laptop    kernel    [  532.238055] ata3: EH complete
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623306] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623315] ata3.00: BMDMA stat 0x24
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623323] ata3.00: failed command: READ DMA
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623340] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623344]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623352] ata3.00: status: { DRDY ERR }
04/14/11 12:19:38 PM    Laptop    kernel    [  534.623358] ata3.00: error: { UNC }
04/14/11 12:19:38 PM    Laptop    kernel    [  534.785007] ata3.00: configured for UDMA/133
04/14/11 12:19:38 PM    Laptop    kernel    [  534.785024] ata3: EH complete
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144622] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144630] ata3.00: BMDMA stat 0x24
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144638] ata3.00: failed command: READ DMA
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144655] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144659]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144667] ata3.00: status: { DRDY ERR }
04/14/11 12:19:40 PM    Laptop    kernel    [  537.144673] ata3.00: error: { UNC }
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296871] ata3.00: configured for UDMA/133
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296894] sd 2:0:0:0: [sda] Unhandled sense code
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296900] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296909] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296920] Descriptor sense data with sense descriptors (in hex):
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296926]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296950]         00 24 28 0e 
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296960] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296974] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 24 28 08 00 00 08 00
04/14/11 12:19:40 PM    Laptop    kernel    [  537.296996] end_request: I/O error, dev sda, sector 2369550
04/14/11 12:19:40 PM    Laptop    kernel    [  537.297023] ata3: EH complete
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908181] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908192] ata3.00: BMDMA stat 0x24
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908201] ata3.00: failed command: READ DMA
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908219] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908223]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908231] ata3.00: status: { DRDY ERR }
04/14/11 12:19:43 PM    Laptop    kernel    [  539.908237] ata3.00: error: { UNC }
04/14/11 12:19:43 PM    Laptop    kernel    [  540.060881] ata3.00: configured for UDMA/133
04/14/11 12:19:43 PM    Laptop    kernel    [  540.060905] ata3: EH complete
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484556] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484567] ata3.00: BMDMA stat 0x24
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484576] ata3.00: failed command: READ DMA
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484593] ata3.00: cmd c8/00:08:08:28:24/00:00:00:00:00/e0 tag 0 dma 4096 in
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484597]          res 51/40:00:0e:28:24/00:00:00:00:00/00 Emask 0x9 (media error)
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484605] ata3.00: status: { DRDY ERR }
04/14/11 12:19:46 PM    Laptop    kernel    [  542.484611] ata3.00: error: { UNC }
04/14/11 12:19:46 PM    Laptop    kernel    [  542.636928] ata3.00: configured for UDMA/133
04/14/11 12:19:46 PM    Laptop    kernel    [  542.636950] ata3: EH complete

---

