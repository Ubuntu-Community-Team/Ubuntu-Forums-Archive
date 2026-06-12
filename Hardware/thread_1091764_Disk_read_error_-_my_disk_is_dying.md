---
title: "Disk read error - my disk is dying?"
date: 2009-03-09
forum: Hardware
---

### Post by kajaman on 2009-03-09
Hi guys,

Today, when I tried to start firefox, the error happened and it didn't start. Apparently there is disk error, and dmesg is showing:
> 
[  198.184551] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0                               
[  198.184561] ata3.00: irq_stat 0x40000008                                                            
[  198.184568] ata3.00: cmd 60/08:08:36:40:91/00:00:06:00:00/40 tag 1 ncq 4096 in                      
[  198.184570]          res 51/40:08:36:40:91/03:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  198.184575] ata3.00: status: { DRDY ERR }                                                           
[  198.184578] ata3.00: error: { UNC }                                                                 
[  198.187099] ata3.00: configured for UDMA/100                                                        
[  198.187126] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK            
[  198.187130] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]                       
[  198.187135] Descriptor sense data with sense descriptors (in hex):                                  
[  198.187138]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00                                 
[  198.187149]         06 91 40 36                                                                     
[  198.187154] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed           
[  198.187159] end_request: I/O error, dev sda, sector 110182454                                       
[  198.187178] ata3: EH complete                                                                       
[  198.187215] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  198.187231] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  198.187233] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  198.187259] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  262.771347] FAT: Filesystem panic (dev sdb2)                                                        
[  262.771355]     invalid access to FAT (entry 0x0dddddbd)                                            
[  262.771360]     File system has been set read-only                                                  
[  412.662104] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0                               
[  412.662113] ata3.00: irq_stat 0x40000008                                                            
[  412.662121] ata3.00: cmd 60/08:00:36:40:91/00:00:06:00:00/40 tag 0 ncq 4096 in                      
[  412.662123]          res 51/40:08:36:40:91/03:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  412.662128] ata3.00: status: { DRDY ERR }                                                           
[  412.662131] ata3.00: error: { UNC }                                                                 
[  412.666047] ata3.00: configured for UDMA/100                                                        
[  412.666061] ata3: EH complete                                                                       
[  412.666125] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  412.666142] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  412.666145] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  412.666171] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  416.602640] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0                               
[  416.602649] ata3.00: irq_stat 0x40000008                                                            
[  416.602657] ata3.00: cmd 60/08:00:36:40:91/00:00:06:00:00/40 tag 0 ncq 4096 in                      
[  416.602659]          res 51/40:08:36:40:91/02:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  416.602664] ata3.00: status: { DRDY ERR }                                                           
[  416.602666] ata3.00: error: { UNC }                                                                 
[  416.605513] ata3.00: configured for UDMA/100                                                        
[  416.605532] ata3: EH complete                                                                       
[  416.605647] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  416.605675] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  416.605679] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  416.605723] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  420.592279] ata3.00: exception Emask 0x0 SAct 0xd SErr 0x0 action 0x0                               
[  420.592289] ata3.00: irq_stat 0x40000008                                                            
[  420.592297] ata3.00: cmd 60/08:18:36:40:91/00:00:06:00:00/40 tag 3 ncq 4096 in                      
[  420.592299]          res 51/40:08:36:40:91/02:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  420.592303] ata3.00: status: { DRDY ERR }                                                           
[  420.592306] ata3.00: error: { UNC }                                                                 
[  420.594809] ata3.00: configured for UDMA/100                                                        
[  420.594826] ata3: EH complete                                                                       
[  420.594906] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  420.594935] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  420.594939] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  420.594984] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  424.526372] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0                               
[  424.526382] ata3.00: irq_stat 0x40000008                                                            
[  424.526390] ata3.00: cmd 60/08:00:36:40:91/00:00:06:00:00/40 tag 0 ncq 4096 in                      
[  424.526392]          res 51/40:08:36:40:91/02:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  424.526396] ata3.00: status: { DRDY ERR }                                                           
[  424.526400] ata3.00: error: { UNC }                                                                 
[  424.528976] ata3.00: configured for UDMA/100                                                        
[  424.528988] ata3: EH complete                                                                       
[  424.529043] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  424.529061] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  424.529064] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  424.529091] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  428.482681] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0                               
[  428.482688] ata3.00: irq_stat 0x40000008                                                            
[  428.482693] ata3.00: cmd 60/08:10:36:40:91/00:00:06:00:00/40 tag 2 ncq 4096 in                      
[  428.482694]          res 51/40:08:36:40:91/02:00:06:00:00/40 Emask 0x409 (media error) <F>          
[  428.482697] ata3.00: status: { DRDY ERR }                                                           
[  428.482699] ata3.00: error: { UNC }                                                                 
[  428.485202] ata3.00: configured for UDMA/100                                                        
[  428.485219] ata3: EH complete                                                                       
[  428.485296] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)                       
[  428.485325] sd 2:0:0:0: [sda] Write Protect is off                                                  
[  428.485329] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                               
[  428.485373] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[  432.416840] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  432.416849] ata3.00: irq_stat 0x40000008
[  432.416857] ata3.00: cmd 60/08:00:36:40:91/00:00:06:00:00/40 tag 0 ncq 4096 in
[  432.416859]          res 51/40:08:36:40:91/02:00:06:00:00/40 Emask 0x409 (media error) <F>
[  432.416864] ata3.00: status: { DRDY ERR }
[  432.416866] ata3.00: error: { UNC }
[  432.419375] ata3.00: configured for UDMA/100
[  432.419393] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  432.419399] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  432.419407] Descriptor sense data with sense descriptors (in hex):
[  432.419411]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  432.419430]         06 91 40 36
[  432.419438] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  432.419446] end_request: I/O error, dev sda, sector 110182454
[  432.419473] ata3: EH complete
[  432.419533] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  432.419558] sd 2:0:0:0: [sda] Write Protect is off
[  432.419562] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  432.419604] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


Is this my disk dying? I am making copy of data right now, but I would be happy to hear it's some kernel issue rather my disk coing corrupt...

Thanks,
Hubert

---

