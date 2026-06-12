---
title: "repeated hangs and ata action frozen errors on ibex w/ sw raid"
date: 2009-02-24
forum: Hardware
---

### Post by belgarth on 2009-02-24
Hi all,

I recently added a 750 GB ST3750640AS Seagate hard drive to my western digital WD7500AAKS-00RBA0 using Linux software raid. Since then I have had random hangs due to high cpu due to high IO wait. The kernel log shows the following:

-----------------------------------------------------------
Feb 24 18:50:10 media-server kernel: [ 2252.584049] ata5.00: exception Emask 0x0 SAct 0xfff SErr 0x0 action 0x6 frozen    
Feb 24 18:50:11 media-server kernel: [ 2252.584073] ata5.00: cmd 60/28:00:14:db:18/00:00:3c:00:00/40 tag 0 ncq 20480 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584080]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584092] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584101] ata5.00: cmd 60/58:08:e4:2c:19/00:00:3c:00:00/40 tag 1 ncq 45056 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584104]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584110] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584119] ata5.00: cmd 60/20:10:7c:e8:19/00:00:3c:00:00/40 tag 2 ncq 16384 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584122]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584128] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584139] ata5.00: cmd 60/00:18:2d:31:33/01:00:00:00:00/40 tag 3 ncq 131072 in  
Feb 24 18:50:11 media-server kernel: [ 2252.584142]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584149] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584158] ata5.00: cmd 60/40:20:7c:fb:1b/00:00:3c:00:00/40 tag 4 ncq 32768 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584165]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584175] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584184] ata5.00: cmd 60/60:28:b4:55:14/00:00:3c:00:00/40 tag 5 ncq 49152 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584191]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584201] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584210] ata5.00: cmd 60/58:30:dc:fb:1b/00:00:3c:00:00/40 tag 6 ncq 45056 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584216]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584227] ata5.00: status: { DRDY }                                             
Feb 24 18:50:11 media-server kernel: [ 2252.584235] ata5.00: cmd 60/18:38:fc:da:18/00:00:3c:00:00/40 tag 7 ncq 12288 in   
Feb 24 18:50:11 media-server kernel: [ 2252.584242]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:11 media-server kernel: [ 2252.584253] ata5.00: status: { DRDY }                                             
Feb 24 18:50:13 media-server kernel: [ 2252.584262] ata5.00: cmd 60/00:40:2d:32:33/01:00:00:00:00/40 tag 8 ncq 131072 in  
Feb 24 18:50:13 media-server kernel: [ 2252.584268]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:13 media-server kernel: [ 2252.584278] ata5.00: status: { DRDY }                                             
Feb 24 18:50:13 media-server kernel: [ 2252.584287] ata5.00: cmd 60/08:48:45:56:23/00:00:00:00:00/40 tag 9 ncq 4096 in    
Feb 24 18:50:13 media-server kernel: [ 2252.584294]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:13 media-server kernel: [ 2252.584304] ata5.00: status: { DRDY }                                             
Feb 24 18:50:13 media-server kernel: [ 2252.584312] ata5.00: cmd 60/08:50:ed:56:23/00:00:00:00:00/40 tag 10 ncq 4096 in   
Feb 24 18:50:13 media-server kernel: [ 2252.584315]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:13 media-server kernel: [ 2252.584322] ata5.00: status: { DRDY }                                             
Feb 24 18:50:13 media-server kernel: [ 2252.584330] ata5.00: cmd 60/08:58:54:48:83/00:00:3a:00:00/40 tag 11 ncq 4096 in   
Feb 24 18:50:13 media-server kernel: [ 2252.584333]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)  
Feb 24 18:50:13 media-server kernel: [ 2252.584339] ata5.00: status: { DRDY }                                             
Feb 24 18:50:13 media-server kernel: [ 2252.584351] ata5: hard resetting link                                             
Feb 24 18:50:13 media-server kernel: [ 2253.072037] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                
Feb 24 18:50:13 media-server kernel: [ 2253.090810] ata5.00: configured for UDMA/133                                      
Feb 24 18:50:13 media-server kernel: [ 2253.090867] ata5: EH complete                                                     
Feb 24 18:50:13 media-server kernel: [ 2253.091042] sd 4:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)    
Feb 24 18:50:13 media-server kernel: [ 2253.091081] sd 4:0:0:0: [sda] Write Protect is off                                
Feb 24 18:50:13 media-server kernel: [ 2253.091092] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00                             
Feb 24 18:50:13 media-server kernel: [ 2253.091146] sd 4:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't\
 support DPO or FUA                                                                                 
-------------------------------------------------------------

I have tried to find some explanation of these errors and have found situations where the dvd rom drive was the problem and have removed mine and the problem persists. I also found people with a similar problem with the Seagate 1.5TB drive firmware having to do with the write cache, but I disabled the write cache and the problem persists.

At the least I would like to know how I can check which device ata5.00 refers to so I can confirm if the problem is with the Seagate drive like I suspect.

The system has a AN-M2HD motherboard and 2 Gigs of RAM. It is mostly used as a mythtv frontend and backend. It is currently running 8.10 32 bit, but the problem was also seen on 64 bit. The problem seems to be more frequent the more intense the harddrive use is, but seems to also occur when nothing much is going on.

I would appreciate any help someone can provide.

---

### Post by belgarth on 2009-02-24
I realize now that this should be in the hardware forum instead. When a mod sees this, can he/she please move it?

---

