---
title: "Kernel Crashed - ata1.00: failed command: READ DMA EXT"
date: 2011-10-02
forum: Hardware
---

### Post by dreampen51388 on 2011-10-02
Hi, My Ubuntu suddenly froze. And I saw there were tons of errors on the console. Here is what I found from syslog. Did my hardware 
failed? 

Oct  1 20:31:24 laptop-1 rtkit-daemon[1218]: Supervising 6 threads of 2 processes of 2 users.
Oct  1 20:31:34 laptop-1 gnome-session[1328]: WARNING: Application 'compiz.desktop' failed to register before timeout
Oct  1 20:31:35 laptop-1 ntpdate[1291]: adjust time server 91.189.94.4 offset -0.021553 sec
Oct  1 20:32:08 laptop-1 kernel: [   79.536017] CE: hpet increased min_delta_ns to 11520 nsec
Oct  1 20:32:20 laptop-1 kernel: [   91.426035] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:20 laptop-1 kernel: [   91.426048] ata1.00: BMDMA stat 0x4
Oct  1 20:32:20 laptop-1 kernel: [   91.426059] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:20 laptop-1 kernel: [   91.426078] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:20 laptop-1 kernel: [   91.426082]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:20 laptop-1 kernel: [   91.426091] ata1.00: status: { DRDY ERR }
Oct  1 20:32:20 laptop-1 kernel: [   91.448269] ata1.00: configured for UDMA/100
Oct  1 20:32:20 laptop-1 kernel: [   91.448301] ata1: EH complete
Oct  1 20:32:24 laptop-1 kernel: [   95.812599] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:24 laptop-1 kernel: [   95.812610] ata1.00: BMDMA stat 0x4
Oct  1 20:32:24 laptop-1 kernel: [   95.812620] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:24 laptop-1 kernel: [   95.812638] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:24 laptop-1 kernel: [   95.812642]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:24 laptop-1 kernel: [   95.812650] ata1.00: status: { DRDY ERR }
Oct  1 20:32:24 laptop-1 kernel: [   95.836268] ata1.00: configured for UDMA/100
Oct  1 20:32:24 laptop-1 kernel: [   95.836306] ata1: EH complete
Oct  1 20:32:29 laptop-1 kernel: [  100.199162] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:29 laptop-1 kernel: [  100.199170] ata1.00: BMDMA stat 0x4
Oct  1 20:32:29 laptop-1 kernel: [  100.199178] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:29 laptop-1 kernel: [  100.199195] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:29 laptop-1 kernel: [  100.199199]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:29 laptop-1 kernel: [  100.199207] ata1.00: status: { DRDY ERR }
Oct  1 20:32:29 laptop-1 kernel: [  100.220275] ata1.00: configured for UDMA/100
Oct  1 20:32:29 laptop-1 kernel: [  100.220313] ata1: EH complete
Oct  1 20:32:33 laptop-1 kernel: [  104.596868] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:33 laptop-1 kernel: [  104.596877] ata1.00: BMDMA stat 0x4
Oct  1 20:32:33 laptop-1 kernel: [  104.596885] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:33 laptop-1 kernel: [  104.596903] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:33 laptop-1 kernel: [  104.596907]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:33 laptop-1 kernel: [  104.596915] ata1.00: status: { DRDY ERR }
Oct  1 20:32:33 laptop-1 kernel: [  104.620273] ata1.00: configured for UDMA/100
Oct  1 20:32:33 laptop-1 kernel: [  104.620311] ata1: EH complete
Oct  1 20:32:37 laptop-1 kernel: [  108.983477] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:37 laptop-1 kernel: [  108.983490] ata1.00: BMDMA stat 0x4
Oct  1 20:32:37 laptop-1 kernel: [  108.983501] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:37 laptop-1 kernel: [  108.983520] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:37 laptop-1 kernel: [  108.983523]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:37 laptop-1 kernel: [  108.983532] ata1.00: status: { DRDY ERR }
Oct  1 20:32:37 laptop-1 kernel: [  109.004273] ata1.00: configured for UDMA/100
Oct  1 20:32:37 laptop-1 kernel: [  109.004311] ata1: EH complete
Oct  1 20:32:42 laptop-1 kernel: [  113.493043] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:42 laptop-1 kernel: [  113.493052] ata1.00: BMDMA stat 0x4
Oct  1 20:32:42 laptop-1 kernel: [  113.493060] ata1.00: failed command: READ DMA EXT
Oct  1 20:32:42 laptop-1 kernel: [  113.493077] ata1.00: cmd 25/00:00:90:9e:04/00:04:05:00:00/e0 tag 0 dma 524288 in
Oct  1 20:32:42 laptop-1 kernel: [  113.493080]          res 51/01:b9:d7:9e:04/01:03:05:00:00/e0 Emask 0x1 (device error)
Oct  1 20:32:42 laptop-1 kernel: [  113.493089] ata1.00: status: { DRDY ERR }
Oct  1 20:32:42 laptop-1 kernel: [  113.516275] ata1.00: configured for UDMA/100
Oct  1 20:32:42 laptop-1 kernel: [  113.516325] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:32:42 laptop-1 kernel: [  113.516332] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:32:42 laptop-1 kernel: [  113.516343] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:32:42 laptop-1 kernel: [  113.516356] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:32:42 laptop-1 kernel: [  113.516362]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:32:42 laptop-1 kernel: [  113.516387]         05 04 9e d7 
Oct  1 20:32:42 laptop-1 kernel: [  113.516398] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:32:42 laptop-1 kernel: [  113.516413] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e 90 00 04 00 00
Oct  1 20:32:42 laptop-1 kernel: [  113.516435] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:32:42 laptop-1 kernel: [  113.516539] ata1: EH complete
Oct  1 20:32:47 laptop-1 kernel: [  118.978450] ata1: limiting SATA link speed to 1.5 Gbps
Oct  1 20:32:47 laptop-1 kernel: [  118.978466] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Oct  1 20:32:47 laptop-1 kernel: [  118.978475] ata1.00: BMDMA stat 0x4
Oct  1 20:32:47 laptop-1 kernel: [  118.978485] ata1.00: failed command: READ DMA
Oct  1 20:32:47 laptop-1 kernel: [  118.978504] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:32:47 laptop-1 kernel: [  118.978508]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:32:47 laptop-1 kernel: [  118.978517] ata1.00: status: { DRDY ERR }
Oct  1 20:32:47 laptop-1 kernel: [  118.978531] ata1: hard resetting link
Oct  1 20:32:47 laptop-1 kernel: [  118.978537] ata1: nv: skipping hardreset on occupied port
Oct  1 20:32:48 laptop-1 kernel: [  119.444082] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  1 20:32:48 laptop-1 kernel: [  119.468306] ata1.00: configured for UDMA/100
Oct  1 20:32:48 laptop-1 kernel: [  119.468330] ata1: EH complete
Oct  1 20:32:52 laptop-1 kernel: [  123.844999] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:52 laptop-1 kernel: [  123.845011] ata1.00: BMDMA stat 0x4
Oct  1 20:32:52 laptop-1 kernel: [  123.845022] ata1.00: failed command: READ DMA
Oct  1 20:32:52 laptop-1 kernel: [  123.845041] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:32:52 laptop-1 kernel: [  123.845045]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:32:52 laptop-1 kernel: [  123.845054] ata1.00: status: { DRDY ERR }
Oct  1 20:32:52 laptop-1 kernel: [  123.868328] ata1.00: configured for UDMA/100
Oct  1 20:32:52 laptop-1 kernel: [  123.868372] ata1: EH complete
Oct  1 20:32:57 laptop-1 kernel: [  128.233784] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:32:57 laptop-1 kernel: [  128.233796] ata1.00: BMDMA stat 0x4
Oct  1 20:32:57 laptop-1 kernel: [  128.233807] ata1.00: failed command: READ DMA
Oct  1 20:32:57 laptop-1 kernel: [  128.233826] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:32:57 laptop-1 kernel: [  128.233830]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:32:57 laptop-1 kernel: [  128.233839] ata1.00: status: { DRDY ERR }
Oct  1 20:32:57 laptop-1 kernel: [  128.256272] ata1.00: configured for UDMA/100
Oct  1 20:32:57 laptop-1 kernel: [  128.256310] ata1: EH complete
Oct  1 20:33:01 laptop-1 kernel: [  132.633664] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:01 laptop-1 kernel: [  132.633677] ata1.00: BMDMA stat 0x4
Oct  1 20:33:01 laptop-1 kernel: [  132.633687] ata1.00: failed command: READ DMA
Oct  1 20:33:01 laptop-1 kernel: [  132.633707] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:01 laptop-1 kernel: [  132.633710]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:01 laptop-1 kernel: [  132.633719] ata1.00: status: { DRDY ERR }
Oct  1 20:33:01 laptop-1 kernel: [  132.656275] ata1.00: configured for UDMA/100
Oct  1 20:33:01 laptop-1 kernel: [  132.656315] ata1: EH complete
Oct  1 20:33:05 laptop-1 kernel: [  137.155771] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:05 laptop-1 kernel: [  137.155783] ata1.00: BMDMA stat 0x4
Oct  1 20:33:05 laptop-1 kernel: [  137.155792] ata1.00: failed command: READ DMA
Oct  1 20:33:05 laptop-1 kernel: [  137.155811] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:05 laptop-1 kernel: [  137.155815]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:05 laptop-1 kernel: [  137.155823] ata1.00: status: { DRDY ERR }
Oct  1 20:33:06 laptop-1 kernel: [  137.176269] ata1.00: configured for UDMA/100
Oct  1 20:33:06 laptop-1 kernel: [  137.176308] ata1: EH complete
Oct  1 20:33:10 laptop-1 kernel: [  141.555712] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:10 laptop-1 kernel: [  141.555724] ata1.00: BMDMA stat 0x4
Oct  1 20:33:10 laptop-1 kernel: [  141.555734] ata1.00: failed command: READ DMA
Oct  1 20:33:10 laptop-1 kernel: [  141.555753] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:10 laptop-1 kernel: [  141.555757]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:10 laptop-1 kernel: [  141.555766] ata1.00: status: { DRDY ERR }
Oct  1 20:33:10 laptop-1 kernel: [  141.576269] ata1.00: configured for UDMA/100
Oct  1 20:33:10 laptop-1 kernel: [  141.576312] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:33:10 laptop-1 kernel: [  141.576320] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:33:10 laptop-1 kernel: [  141.576332] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:33:10 laptop-1 kernel: [  141.576345] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:33:10 laptop-1 kernel: [  141.576351]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:33:10 laptop-1 kernel: [  141.576376]         05 04 9e d7 
Oct  1 20:33:10 laptop-1 kernel: [  141.576387] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:33:10 laptop-1 kernel: [  141.576401] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:33:10 laptop-1 kernel: [  141.576424] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:33:10 laptop-1 kernel: [  141.576488] ata1: EH complete
Oct  1 20:33:14 laptop-1 kernel: [  146.111104] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:14 laptop-1 kernel: [  146.111118] ata1.00: BMDMA stat 0x4
Oct  1 20:33:14 laptop-1 kernel: [  146.111128] ata1.00: failed command: READ DMA
Oct  1 20:33:14 laptop-1 kernel: [  146.111148] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:14 laptop-1 kernel: [  146.111151]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:14 laptop-1 kernel: [  146.111160] ata1.00: status: { DRDY ERR }
Oct  1 20:33:14 laptop-1 kernel: [  146.132278] ata1.00: configured for UDMA/100
Oct  1 20:33:14 laptop-1 kernel: [  146.132312] ata1: EH complete
Oct  1 20:33:19 laptop-1 kernel: [  150.499963] ata1.00: limiting speed to UDMA/66:PIO4
Oct  1 20:33:19 laptop-1 kernel: [  150.499973] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Oct  1 20:33:19 laptop-1 kernel: [  150.499980] ata1.00: BMDMA stat 0x4
Oct  1 20:33:19 laptop-1 kernel: [  150.499987] ata1.00: failed command: READ DMA
Oct  1 20:33:19 laptop-1 kernel: [  150.500004] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:19 laptop-1 kernel: [  150.500008]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:19 laptop-1 kernel: [  150.500053] ata1.00: status: { DRDY ERR }
Oct  1 20:33:19 laptop-1 kernel: [  150.500069] ata1: hard resetting link
Oct  1 20:33:19 laptop-1 kernel: [  150.500078] ata1: nv: skipping hardreset on occupied port
Oct  1 20:33:19 laptop-1 kernel: [  150.968067] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  1 20:33:19 laptop-1 kernel: [  151.016273] ata1.00: configured for UDMA/66
Oct  1 20:33:19 laptop-1 kernel: [  151.016290] ata1: EH complete
Oct  1 20:33:24 laptop-1 kernel: [  155.399847] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:24 laptop-1 kernel: [  155.399858] ata1.00: BMDMA stat 0x4
Oct  1 20:33:24 laptop-1 kernel: [  155.399867] ata1.00: failed command: READ DMA
Oct  1 20:33:24 laptop-1 kernel: [  155.399885] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:24 laptop-1 kernel: [  155.399889]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:24 laptop-1 kernel: [  155.399898] ata1.00: status: { DRDY ERR }
Oct  1 20:33:24 laptop-1 kernel: [  155.424267] ata1.00: configured for UDMA/66
Oct  1 20:33:24 laptop-1 kernel: [  155.424304] ata1: EH complete
Oct  1 20:33:28 laptop-1 kernel: [  159.921905] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:28 laptop-1 kernel: [  159.921915] ata1.00: BMDMA stat 0x4
Oct  1 20:33:28 laptop-1 kernel: [  159.921924] ata1.00: failed command: READ DMA
Oct  1 20:33:28 laptop-1 kernel: [  159.921941] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:28 laptop-1 kernel: [  159.921945]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:28 laptop-1 kernel: [  159.921954] ata1.00: status: { DRDY ERR }
Oct  1 20:33:28 laptop-1 kernel: [  159.944272] ata1.00: configured for UDMA/66
Oct  1 20:33:28 laptop-1 kernel: [  159.944288] ata1: EH complete
Oct  1 20:33:33 laptop-1 kernel: [  164.321770] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:33 laptop-1 kernel: [  164.321778] ata1.00: BMDMA stat 0x4
Oct  1 20:33:33 laptop-1 kernel: [  164.321785] ata1.00: failed command: READ DMA
Oct  1 20:33:33 laptop-1 kernel: [  164.321802] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:33 laptop-1 kernel: [  164.321806]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:33 laptop-1 kernel: [  164.321814] ata1.00: status: { DRDY ERR }
Oct  1 20:33:33 laptop-1 kernel: [  164.344265] ata1.00: configured for UDMA/66
Oct  1 20:33:33 laptop-1 kernel: [  164.344298] ata1: EH complete
Oct  1 20:33:37 laptop-1 kernel: [  168.722213] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:37 laptop-1 kernel: [  168.722221] ata1.00: BMDMA stat 0x4
Oct  1 20:33:37 laptop-1 kernel: [  168.722228] ata1.00: failed command: READ DMA
Oct  1 20:33:37 laptop-1 kernel: [  168.722246] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:37 laptop-1 kernel: [  168.722249]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:37 laptop-1 kernel: [  168.722257] ata1.00: status: { DRDY ERR }
Oct  1 20:33:37 laptop-1 kernel: [  168.744262] ata1.00: configured for UDMA/66
Oct  1 20:33:37 laptop-1 kernel: [  168.744292] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:33:37 laptop-1 kernel: [  168.744299] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:33:37 laptop-1 kernel: [  168.744315] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:33:37 laptop-1 kernel: [  168.744328] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:33:37 laptop-1 kernel: [  168.744334]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:33:37 laptop-1 kernel: [  168.744358]         05 04 9e d7 
Oct  1 20:33:37 laptop-1 kernel: [  168.744370] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:33:37 laptop-1 kernel: [  168.744384] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:33:37 laptop-1 kernel: [  168.744406] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:33:37 laptop-1 kernel: [  168.744467] ata1: EH complete
Oct  1 20:33:42 laptop-1 kernel: [  173.288348] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:42 laptop-1 kernel: [  173.288361] ata1.00: BMDMA stat 0x4
Oct  1 20:33:42 laptop-1 kernel: [  173.288371] ata1.00: failed command: READ DMA
Oct  1 20:33:42 laptop-1 kernel: [  173.288391] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:42 laptop-1 kernel: [  173.288394]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:42 laptop-1 kernel: [  173.288403] ata1.00: status: { DRDY ERR }
Oct  1 20:33:42 laptop-1 kernel: [  173.312264] ata1.00: configured for UDMA/66
Oct  1 20:33:42 laptop-1 kernel: [  173.312297] ata1: EH complete
Oct  1 20:33:46 laptop-1 kernel: [  177.688147] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:46 laptop-1 kernel: [  177.688154] ata1.00: BMDMA stat 0x4
Oct  1 20:33:46 laptop-1 kernel: [  177.688161] ata1.00: failed command: READ DMA
Oct  1 20:33:46 laptop-1 kernel: [  177.688179] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:46 laptop-1 kernel: [  177.688182]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:46 laptop-1 kernel: [  177.688191] ata1.00: status: { DRDY ERR }
Oct  1 20:33:46 laptop-1 kernel: [  177.712262] ata1.00: configured for UDMA/66
Oct  1 20:33:46 laptop-1 kernel: [  177.712279] ata1: EH complete
Oct  1 20:33:51 laptop-1 kernel: [  182.210178] ata1.00: limiting speed to UDMA/33:PIO4
Oct  1 20:33:51 laptop-1 kernel: [  182.210188] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Oct  1 20:33:51 laptop-1 kernel: [  182.210195] ata1.00: BMDMA stat 0x4
Oct  1 20:33:51 laptop-1 kernel: [  182.210203] ata1.00: failed command: READ DMA
Oct  1 20:33:51 laptop-1 kernel: [  182.210220] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:51 laptop-1 kernel: [  182.210224]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:51 laptop-1 kernel: [  182.210232] ata1.00: status: { DRDY ERR }
Oct  1 20:33:51 laptop-1 kernel: [  182.210245] ata1: hard resetting link
Oct  1 20:33:51 laptop-1 kernel: [  182.210251] ata1: nv: skipping hardreset on occupied port
Oct  1 20:33:51 laptop-1 kernel: [  182.676058] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct  1 20:33:51 laptop-1 kernel: [  182.740274] ata1.00: configured for UDMA/33
Oct  1 20:33:51 laptop-1 kernel: [  182.740306] ata1: EH complete
Oct  1 20:33:55 laptop-1 kernel: [  187.110068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:33:55 laptop-1 kernel: [  187.110075] ata1.00: BMDMA stat 0x4
Oct  1 20:33:55 laptop-1 kernel: [  187.110081] ata1.00: failed command: READ DMA
Oct  1 20:33:55 laptop-1 kernel: [  187.110099] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:33:55 laptop-1 kernel: [  187.110102]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:33:55 laptop-1 kernel: [  187.110110] ata1.00: status: { DRDY ERR }
Oct  1 20:33:55 laptop-1 kernel: [  187.132260] ata1.00: configured for UDMA/33
Oct  1 20:33:55 laptop-1 kernel: [  187.132276] ata1: EH complete
Oct  1 20:34:00 laptop-1 kernel: [  191.509987] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:00 laptop-1 kernel: [  191.509994] ata1.00: BMDMA stat 0x4
Oct  1 20:34:00 laptop-1 kernel: [  191.510001] ata1.00: failed command: READ DMA
Oct  1 20:34:00 laptop-1 kernel: [  191.510018] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:00 laptop-1 kernel: [  191.510022]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:00 laptop-1 kernel: [  191.510030] ata1.00: status: { DRDY ERR }
Oct  1 20:34:00 laptop-1 kernel: [  191.532260] ata1.00: configured for UDMA/33
Oct  1 20:34:00 laptop-1 kernel: [  191.532277] ata1: EH complete
Oct  1 20:34:04 laptop-1 kernel: [  195.898767] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:04 laptop-1 kernel: [  195.898780] ata1.00: BMDMA stat 0x4
Oct  1 20:34:04 laptop-1 kernel: [  195.898790] ata1.00: failed command: READ DMA
Oct  1 20:34:04 laptop-1 kernel: [  195.898809] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:04 laptop-1 kernel: [  195.898813]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:04 laptop-1 kernel: [  195.898822] ata1.00: status: { DRDY ERR }
Oct  1 20:34:04 laptop-1 kernel: [  195.920279] ata1.00: configured for UDMA/33
Oct  1 20:34:04 laptop-1 kernel: [  195.920322] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:34:04 laptop-1 kernel: [  195.920330] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:34:04 laptop-1 kernel: [  195.920341] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:34:04 laptop-1 kernel: [  195.920354] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:34:04 laptop-1 kernel: [  195.920361]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:34:04 laptop-1 kernel: [  195.920385]         05 04 9e d7 
Oct  1 20:34:04 laptop-1 kernel: [  195.920397] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:34:04 laptop-1 kernel: [  195.920411] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:34:04 laptop-1 kernel: [  195.920434] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:34:04 laptop-1 kernel: [  195.920502] ata1: EH complete
Oct  1 20:34:18 laptop-1 kernel: [  209.787307] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:18 laptop-1 kernel: [  209.787320] ata1.00: BMDMA stat 0x4
Oct  1 20:34:18 laptop-1 kernel: [  209.787331] ata1.00: failed command: READ DMA
Oct  1 20:34:18 laptop-1 kernel: [  209.787350] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:18 laptop-1 kernel: [  209.787354]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:18 laptop-1 kernel: [  209.787363] ata1.00: status: { DRDY ERR }
Oct  1 20:34:18 laptop-1 kernel: [  209.808304] ata1.00: configured for UDMA/33
Oct  1 20:34:18 laptop-1 kernel: [  209.808343] ata1: EH complete
Oct  1 20:34:23 laptop-1 kernel: [  214.298357] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:23 laptop-1 kernel: [  214.298373] ata1.00: BMDMA stat 0x4
Oct  1 20:34:23 laptop-1 kernel: [  214.298385] ata1.00: failed command: READ DMA
Oct  1 20:34:23 laptop-1 kernel: [  214.298405] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:23 laptop-1 kernel: [  214.298409]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:23 laptop-1 kernel: [  214.298418] ata1.00: status: { DRDY ERR }
Oct  1 20:34:23 laptop-1 kernel: [  214.320413] ata1.00: configured for UDMA/33
Oct  1 20:34:23 laptop-1 kernel: [  214.320463] ata1: EH complete
Oct  1 20:34:27 laptop-1 kernel: [  218.698245] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:27 laptop-1 kernel: [  218.698259] ata1.00: BMDMA stat 0x4
Oct  1 20:34:27 laptop-1 kernel: [  218.698271] ata1.00: failed command: READ DMA
Oct  1 20:34:27 laptop-1 kernel: [  218.698291] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:27 laptop-1 kernel: [  218.698295]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:27 laptop-1 kernel: [  218.698304] ata1.00: status: { DRDY ERR }
Oct  1 20:34:27 laptop-1 kernel: [  218.720530] ata1.00: configured for UDMA/33
Oct  1 20:34:27 laptop-1 kernel: [  218.720583] ata1: EH complete
Oct  1 20:34:31 laptop-1 kernel: [  223.086983] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:31 laptop-1 kernel: [  223.086996] ata1.00: BMDMA stat 0x4
Oct  1 20:34:31 laptop-1 kernel: [  223.087007] ata1.00: failed command: READ DMA
Oct  1 20:34:31 laptop-1 kernel: [  223.087026] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:31 laptop-1 kernel: [  223.087030]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:31 laptop-1 kernel: [  223.087051] ata1.00: status: { DRDY ERR }
Oct  1 20:34:31 laptop-1 kernel: [  223.108367] ata1.00: configured for UDMA/33
Oct  1 20:34:31 laptop-1 kernel: [  223.108421] ata1: EH complete
Oct  1 20:34:36 laptop-1 kernel: [  227.486883] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:36 laptop-1 kernel: [  227.486896] ata1.00: BMDMA stat 0x4
Oct  1 20:34:36 laptop-1 kernel: [  227.486906] ata1.00: failed command: READ DMA
Oct  1 20:34:36 laptop-1 kernel: [  227.486926] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:36 laptop-1 kernel: [  227.486929]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:36 laptop-1 kernel: [  227.486939] ata1.00: status: { DRDY ERR }
Oct  1 20:34:36 laptop-1 kernel: [  227.508293] ata1.00: configured for UDMA/33
Oct  1 20:34:36 laptop-1 kernel: [  227.508335] ata1: EH complete
Oct  1 20:34:40 laptop-1 kernel: [  231.886772] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:40 laptop-1 kernel: [  231.886784] ata1.00: BMDMA stat 0x4
Oct  1 20:34:40 laptop-1 kernel: [  231.886795] ata1.00: failed command: READ DMA
Oct  1 20:34:40 laptop-1 kernel: [  231.886814] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:40 laptop-1 kernel: [  231.886818]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:40 laptop-1 kernel: [  231.886827] ata1.00: status: { DRDY ERR }
Oct  1 20:34:40 laptop-1 kernel: [  231.908388] ata1.00: configured for UDMA/33
Oct  1 20:34:40 laptop-1 kernel: [  231.908456] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:34:40 laptop-1 kernel: [  231.908464] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:34:40 laptop-1 kernel: [  231.908477] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:34:40 laptop-1 kernel: [  231.908491] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:34:40 laptop-1 kernel: [  231.908498]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:34:40 laptop-1 kernel: [  231.908522]         05 04 9e d7 
Oct  1 20:34:40 laptop-1 kernel: [  231.908533] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:34:40 laptop-1 kernel: [  231.908549] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:34:40 laptop-1 kernel: [  231.908574] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:34:40 laptop-1 kernel: [  231.908678] ata1: EH complete
Oct  1 20:34:45 laptop-1 kernel: [  236.464438] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:45 laptop-1 kernel: [  236.464451] ata1.00: BMDMA stat 0x4
Oct  1 20:34:45 laptop-1 kernel: [  236.464461] ata1.00: failed command: READ DMA
Oct  1 20:34:45 laptop-1 kernel: [  236.464481] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:45 laptop-1 kernel: [  236.464485]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:45 laptop-1 kernel: [  236.464494] ata1.00: status: { DRDY ERR }
Oct  1 20:34:45 laptop-1 kernel: [  236.488378] ata1.00: configured for UDMA/33
Oct  1 20:34:45 laptop-1 kernel: [  236.488440] ata1: EH complete
Oct  1 20:34:49 laptop-1 kernel: [  240.853234] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:49 laptop-1 kernel: [  240.853251] ata1.00: BMDMA stat 0x4
Oct  1 20:34:49 laptop-1 kernel: [  240.853263] ata1.00: failed command: READ DMA
Oct  1 20:34:49 laptop-1 kernel: [  240.853283] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:49 laptop-1 kernel: [  240.853287]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:49 laptop-1 kernel: [  240.853296] ata1.00: status: { DRDY ERR }
Oct  1 20:34:49 laptop-1 kernel: [  240.876413] ata1.00: configured for UDMA/33
Oct  1 20:34:49 laptop-1 kernel: [  240.876468] ata1: EH complete
Oct  1 20:34:54 laptop-1 kernel: [  245.253142] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:54 laptop-1 kernel: [  245.253157] ata1.00: BMDMA stat 0x4
Oct  1 20:34:54 laptop-1 kernel: [  245.253170] ata1.00: failed command: READ DMA
Oct  1 20:34:54 laptop-1 kernel: [  245.253190] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:54 laptop-1 kernel: [  245.253193]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:54 laptop-1 kernel: [  245.253202] ata1.00: status: { DRDY ERR }
Oct  1 20:34:54 laptop-1 kernel: [  245.276428] ata1.00: configured for UDMA/33
Oct  1 20:34:54 laptop-1 kernel: [  245.276483] ata1: EH complete
Oct  1 20:34:58 laptop-1 kernel: [  249.641918] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:34:58 laptop-1 kernel: [  249.641933] ata1.00: BMDMA stat 0x4
Oct  1 20:34:58 laptop-1 kernel: [  249.641944] ata1.00: failed command: READ DMA
Oct  1 20:34:58 laptop-1 kernel: [  249.641965] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:34:58 laptop-1 kernel: [  249.641968]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:34:58 laptop-1 kernel: [  249.641977] ata1.00: status: { DRDY ERR }
Oct  1 20:34:58 laptop-1 kernel: [  249.664294] ata1.00: configured for UDMA/33
Oct  1 20:34:58 laptop-1 kernel: [  249.664333] ata1: EH complete
Oct  1 20:35:02 laptop-1 kernel: [  254.041779] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:02 laptop-1 kernel: [  254.041791] ata1.00: BMDMA stat 0x4
Oct  1 20:35:02 laptop-1 kernel: [  254.041802] ata1.00: failed command: READ DMA
Oct  1 20:35:02 laptop-1 kernel: [  254.041822] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:02 laptop-1 kernel: [  254.041826]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:02 laptop-1 kernel: [  254.041835] ata1.00: status: { DRDY ERR }
Oct  1 20:35:02 laptop-1 kernel: [  254.064371] ata1.00: configured for UDMA/33
Oct  1 20:35:02 laptop-1 kernel: [  254.064421] ata1: EH complete
Oct  1 20:35:07 laptop-1 kernel: [  258.563921] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:07 laptop-1 kernel: [  258.563936] ata1.00: BMDMA stat 0x4
Oct  1 20:35:07 laptop-1 kernel: [  258.563949] ata1.00: failed command: READ DMA
Oct  1 20:35:07 laptop-1 kernel: [  258.563970] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:07 laptop-1 kernel: [  258.563973]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:07 laptop-1 kernel: [  258.563982] ata1.00: status: { DRDY ERR }
Oct  1 20:35:07 laptop-1 kernel: [  258.588287] ata1.00: configured for UDMA/33
Oct  1 20:35:07 laptop-1 kernel: [  258.588330] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:35:07 laptop-1 kernel: [  258.588337] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:35:07 laptop-1 kernel: [  258.588350] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:35:07 laptop-1 kernel: [  258.588363] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:35:07 laptop-1 kernel: [  258.588369]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:35:07 laptop-1 kernel: [  258.588394]         05 04 9e d7 
Oct  1 20:35:07 laptop-1 kernel: [  258.588405] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:35:07 laptop-1 kernel: [  258.588419] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:35:07 laptop-1 kernel: [  258.588442] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:35:07 laptop-1 kernel: [  258.588517] ata1: EH complete
Oct  1 20:35:11 laptop-1 kernel: [  262.974901] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:11 laptop-1 kernel: [  262.974914] ata1.00: BMDMA stat 0x4
Oct  1 20:35:11 laptop-1 kernel: [  262.974924] ata1.00: failed command: READ DMA
Oct  1 20:35:11 laptop-1 kernel: [  262.974944] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:11 laptop-1 kernel: [  262.974947]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:11 laptop-1 kernel: [  262.974956] ata1.00: status: { DRDY ERR }
Oct  1 20:35:11 laptop-1 kernel: [  262.996395] ata1.00: configured for UDMA/33
Oct  1 20:35:11 laptop-1 kernel: [  262.996456] ata1: EH complete
Oct  1 20:35:16 laptop-1 kernel: [  267.363703] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:16 laptop-1 kernel: [  267.363718] ata1.00: BMDMA stat 0x4
Oct  1 20:35:16 laptop-1 kernel: [  267.363729] ata1.00: failed command: READ DMA
Oct  1 20:35:16 laptop-1 kernel: [  267.363749] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:16 laptop-1 kernel: [  267.363753]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:16 laptop-1 kernel: [  267.363762] ata1.00: status: { DRDY ERR }
Oct  1 20:35:16 laptop-1 kernel: [  267.384361] ata1.00: configured for UDMA/33
Oct  1 20:35:16 laptop-1 kernel: [  267.384400] ata1: EH complete
Oct  1 20:35:20 laptop-1 kernel: [  271.763603] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:20 laptop-1 kernel: [  271.763617] ata1.00: BMDMA stat 0x4
Oct  1 20:35:20 laptop-1 kernel: [  271.763629] ata1.00: failed command: READ DMA
Oct  1 20:35:20 laptop-1 kernel: [  271.763648] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:20 laptop-1 kernel: [  271.763652]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:20 laptop-1 kernel: [  271.763661] ata1.00: status: { DRDY ERR }
Oct  1 20:35:20 laptop-1 kernel: [  271.784294] ata1.00: configured for UDMA/33
Oct  1 20:35:20 laptop-1 kernel: [  271.784334] ata1: EH complete
Oct  1 20:35:25 laptop-1 kernel: [  276.163484] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:25 laptop-1 kernel: [  276.163499] ata1.00: BMDMA stat 0x4
Oct  1 20:35:25 laptop-1 kernel: [  276.163510] ata1.00: failed command: READ DMA
Oct  1 20:35:25 laptop-1 kernel: [  276.163530] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:25 laptop-1 kernel: [  276.163534]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:25 laptop-1 kernel: [  276.163543] ata1.00: status: { DRDY ERR }
Oct  1 20:35:25 laptop-1 kernel: [  276.184294] ata1.00: configured for UDMA/33
Oct  1 20:35:25 laptop-1 kernel: [  276.184333] ata1: EH complete
Oct  1 20:35:29 laptop-1 kernel: [  280.685621] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:29 laptop-1 kernel: [  280.685638] ata1.00: BMDMA stat 0x4
Oct  1 20:35:29 laptop-1 kernel: [  280.685650] ata1.00: failed command: READ DMA
Oct  1 20:35:29 laptop-1 kernel: [  280.685670] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:29 laptop-1 kernel: [  280.685674]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:29 laptop-1 kernel: [  280.685683] ata1.00: status: { DRDY ERR }
Oct  1 20:35:29 laptop-1 kernel: [  280.708348] ata1.00: configured for UDMA/33
Oct  1 20:35:29 laptop-1 kernel: [  280.708410] ata1: EH complete
Oct  1 20:35:33 laptop-1 kernel: [  285.074371] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:33 laptop-1 kernel: [  285.074385] ata1.00: BMDMA stat 0x4
Oct  1 20:35:33 laptop-1 kernel: [  285.074397] ata1.00: failed command: READ DMA
Oct  1 20:35:33 laptop-1 kernel: [  285.074417] ata1.00: cmd c8/00:08:d0:9e:04/00:00:00:00:00/e5 tag 0 dma 4096 in
Oct  1 20:35:33 laptop-1 kernel: [  285.074421]          res 51/01:01:d7:9e:04/01:03:05:00:00/e5 Emask 0x1 (device error)
Oct  1 20:35:33 laptop-1 kernel: [  285.074430] ata1.00: status: { DRDY ERR }
Oct  1 20:35:33 laptop-1 kernel: [  285.096289] ata1.00: configured for UDMA/33
Oct  1 20:35:33 laptop-1 kernel: [  285.096331] sd 0:0:0:0: [sda] Unhandled sense code
Oct  1 20:35:33 laptop-1 kernel: [  285.096339] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  1 20:35:33 laptop-1 kernel: [  285.096350] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Oct  1 20:35:33 laptop-1 kernel: [  285.096364] Descriptor sense data with sense descriptors (in hex):
Oct  1 20:35:33 laptop-1 kernel: [  285.096371]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  1 20:35:33 laptop-1 kernel: [  285.096395]         05 04 9e d7 
Oct  1 20:35:33 laptop-1 kernel: [  285.096406] sd 0:0:0:0: [sda]  Add. Sense: Address mark not found for data field
Oct  1 20:35:33 laptop-1 kernel: [  285.096420] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 05 04 9e d0 00 00 08 00
Oct  1 20:35:33 laptop-1 kernel: [  285.096443] end_request: I/O error, dev sda, sector 84188887
Oct  1 20:35:33 laptop-1 kernel: [  285.096507] ata1: EH complete
Oct  1 20:35:39 laptop-1 kernel: [  290.563088] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:39 laptop-1 kernel: [  290.563101] ata1.00: BMDMA stat 0x4
Oct  1 20:35:39 laptop-1 kernel: [  290.563112] ata1.00: failed command: READ DMA
Oct  1 20:35:39 laptop-1 kernel: [  290.563131] ata1.00: cmd c8/00:08:70:31:c1/00:00:00:00:00/e4 tag 0 dma 4096 in
Oct  1 20:35:39 laptop-1 kernel: [  290.563135]          res 51/40:01:77:31:c1/01:03:05:00:00/e4 Emask 0x9 (media error)
Oct  1 20:35:39 laptop-1 kernel: [  290.563144] ata1.00: status: { DRDY ERR }
Oct  1 20:35:39 laptop-1 kernel: [  290.563150] ata1.00: error: { UNC }
Oct  1 20:35:39 laptop-1 kernel: [  290.600374] ata1.00: configured for UDMA/33
Oct  1 20:35:39 laptop-1 kernel: [  290.600420] ata1: EH complete
Oct  1 20:35:44 laptop-1 kernel: [  295.163031] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:44 laptop-1 kernel: [  295.163047] ata1.00: BMDMA stat 0x4
Oct  1 20:35:44 laptop-1 kernel: [  295.163059] ata1.00: failed command: READ DMA
Oct  1 20:35:44 laptop-1 kernel: [  295.163079] ata1.00: cmd c8/00:08:70:31:c1/00:00:00:00:00/e4 tag 0 dma 4096 in
Oct  1 20:35:44 laptop-1 kernel: [  295.163083]          res 51/40:01:77:31:c1/01:03:05:00:00/e4 Emask 0x9 (media error)
Oct  1 20:35:44 laptop-1 kernel: [  295.163093] ata1.00: status: { DRDY ERR }
Oct  1 20:35:44 laptop-1 kernel: [  295.163099] ata1.00: error: { UNC }
Oct  1 20:35:44 laptop-1 kernel: [  295.184345] ata1.00: configured for UDMA/33
Oct  1 20:35:44 laptop-1 kernel: [  295.184384] ata1: EH complete
Oct  1 20:35:48 laptop-1 kernel: [  299.751782] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:48 laptop-1 kernel: [  299.751796] ata1.00: BMDMA stat 0x4
Oct  1 20:35:48 laptop-1 kernel: [  299.751807] ata1.00: failed command: READ DMA
Oct  1 20:35:48 laptop-1 kernel: [  299.751826] ata1.00: cmd c8/00:08:70:31:c1/00:00:00:00:00/e4 tag 0 dma 4096 in
Oct  1 20:35:48 laptop-1 kernel: [  299.751830]          res 51/40:01:77:31:c1/01:03:05:00:00/e4 Emask 0x9 (media error)
Oct  1 20:35:48 laptop-1 kernel: [  299.751839] ata1.00: status: { DRDY ERR }
Oct  1 20:35:48 laptop-1 kernel: [  299.751845] ata1.00: error: { UNC }
Oct  1 20:35:48 laptop-1 kernel: [  299.776304] ata1.00: configured for UDMA/33
Oct  1 20:35:48 laptop-1 kernel: [  299.776347] ata1: EH complete
Oct  1 20:35:53 laptop-1 kernel: [  304.462783] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:53 laptop-1 kernel: [  304.462797] ata1.00: BMDMA stat 0x4
Oct  1 20:35:53 laptop-1 kernel: [  304.462808] ata1.00: failed command: READ DMA
Oct  1 20:35:53 laptop-1 kernel: [  304.462828] ata1.00: cmd c8/00:08:70:31:c1/00:00:00:00:00/e4 tag 0 dma 4096 in
Oct  1 20:35:53 laptop-1 kernel: [  304.462832]          res 51/40:01:77:31:c1/01:03:05:00:00/e4 Emask 0x9 (media error)
Oct  1 20:35:53 laptop-1 kernel: [  304.462841] ata1.00: status: { DRDY ERR }
Oct  1 20:35:53 laptop-1 kernel: [  304.462848] ata1.00: error: { UNC }
Oct  1 20:35:53 laptop-1 kernel: [  304.484409] ata1.00: configured for UDMA/33
Oct  1 20:35:53 laptop-1 kernel: [  304.484456] ata1: EH complete
Oct  1 20:35:57 laptop-1 kernel: [  309.051518] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:35:57 laptop-1 kernel: [  309.051530] ata1.00: BMDMA stat 0x4
Oct  1 20:35:57 laptop-1 kernel: [  309.051540] ata1.00: failed command: READ DMA
Oct  1 20:35:57 laptop-1 kernel: [  309.051559] ata1.00: cmd c8/00:08:70:31:c1/00:00:00:00:00/e4 tag 0 dma 4096 in
Oct  1 20:35:57 laptop-1 kernel: [  309.051563]          res 51/40:01:77:31:c1/01:03:05:00:00/e4 Emask 0x9 (media error)
Oct  1 20:35:57 laptop-1 kernel: [  309.051572] ata1.00: status: { DRDY ERR }
Oct  1 20:35:57 laptop-1 kernel: [  309.051578] ata1.00: error: { UNC }
Oct  1 20:35:57 laptop-1 kernel: [  309.072385] ata1.00: configured for UDMA/33
Oct  1 20:35:57 laptop-1 kernel: [  309.072417] ata1: EH complete
Oct  1 20:36:02 laptop-1 kernel: [  313.651461] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  1 20:36:02 laptop-1 kernel: [  313.651478] ata1.00: BMDMA stat 0x4
Oct  1 20:36:02 laptop-1 kernel: [  313.651490] ata1.00: failed command: READ DMA
Oct  1 20:36:02 laptop-1 kernel: [  313.651510

---

### Post by dreampen51388 on 2011-10-02
Not sure ata3.00: BMDMA stat 0x4 
means my DMA controller is bad or hard drive is bad.

---

