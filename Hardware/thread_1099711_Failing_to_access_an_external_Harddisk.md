---
title: "Failing to access an external Harddisk"
date: 2009-03-18
forum: Hardware
---

### Post by Calida on 2009-03-18
I have a huge problem with one of my exteranal HD, a Wester Digital WD10EACS-00ZJB0

Since an hour ago it worked fine, i could read and write to and from it and now I get the following when I try to connect it to my PC:

> 
[19297.108517] usb 4-1: new high speed USB device using ehci_hcd and address 5                                                                                           
[19297.243466] usb 4-1: configuration #1 chosen from 1 choice                                                                                                            
[19297.244314] scsi9 : SCSI emulation for USB Mass Storage devices                                                                                                       
[19297.245269] usb-storage: device found at 5                                                                                                                            
[19297.245273] usb-storage: waiting for device to settle before scanning                                                                                                 
[19302.245729] usb-storage: device scan complete                                                                                                                         
[19302.246207] scsi 9:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS                                                                          
[19302.247075] sd 9:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).                                                                                       
[19302.249698] sd 9:0:0:0: [sdd] READ CAPACITY(16) failed                                                                                                                
[19302.249703] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19302.249706] sd 9:0:0:0: [sdd] Use 0xffffffff as device size                                                                                                           
[19302.249709] sd 9:0:0:0: [sdd] 4294967296 512-byte hardware sectors (2199023 MB)                                                                                       
[19302.250451] sd 9:0:0:0: [sdd] Write Protect is off                                                                                                                    
[19302.250453] sd 9:0:0:0: [sdd] Mode Sense: 34 00 00 00                                                                                                                 
[19302.250455] sd 9:0:0:0: [sdd] Assuming drive cache: write through                                                                                                     
[19302.251072] sd 9:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).                                                                                       
[19302.263934] sd 9:0:0:0: [sdd] READ CAPACITY(16) failed                                                                                                                
[19302.263939] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19302.263943] sd 9:0:0:0: [sdd] Use 0xffffffff as device size                                                                                                           
[19302.263946] sd 9:0:0:0: [sdd] 4294967296 512-byte hardware sectors (2199023 MB)                                                                                       
[19302.265034] sd 9:0:0:0: [sdd] Write Protect is off                                                                                                                    
[19302.265038] sd 9:0:0:0: [sdd] Mode Sense: 34 00 00 00                                                                                                                 
[19302.265040] sd 9:0:0:0: [sdd] Assuming drive cache: write through                                                                                                     
[19302.265045]  sdd:<6>sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                      
[19313.660780] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19313.660785] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19313.660789] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19313.660794] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19325.461852] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19325.461860] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19325.461864] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19325.461868] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19325.461872] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19337.257431] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19337.257438] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19337.257442] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19337.257445] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19337.257450] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19349.053139] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19349.053146] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19349.053150] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19349.053154] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19349.053159] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19360.848965] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19360.848972] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19360.848976] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19360.848980] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19360.848985] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19360.848995] ldm_validate_partition_table(): Disk read failed.                                                                                                         
[19372.656798] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19372.656806] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19372.656811] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19372.656816] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19372.656821] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19384.452877] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19384.452885] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19384.452891] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19384.452895] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19384.452900] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19396.260957] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19396.260964] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19396.260967] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19396.260971] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19396.260976] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19408.056911] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19408.056918] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19408.056924] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19408.056928] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19408.056933] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19408.056950] Dev sdd: unable to read RDB block 0                                                                                                                       
[19419.864995] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19419.865001] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19419.865004] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19419.865007] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19419.865011] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19431.661316] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19431.661323] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19431.661327] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19431.661331] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19431.661335] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19443.469396] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19443.469404] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19443.469408] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19443.469412] end_request: I/O error, dev sdd, sector 24                                                                                                                
[19443.469417] Buffer I/O error on device sdd, logical block 3                                                                                                           
[19455.265603] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19455.265611] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19455.265614] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19455.265619] end_request: I/O error, dev sdd, sector 24                                                                                                                
[19455.265623] Buffer I/O error on device sdd, logical block 3                                                                                                           
[19467.073679] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19467.073686] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19467.073690] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19467.073694] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19467.073699] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19478.870009] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19478.870016] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19478.870020] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19478.870024] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19478.870028] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19478.870043]  unable to read partition table                                                                                                                           
[19478.870837] sd 9:0:0:0: [sdd] Attached SCSI disk                                                                                                                      
[19478.872258] sd 9:0:0:0: Attached scsi generic sg4 type 0                                                                                                              
[19490.718595] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                              
[19490.718604] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]                                                                                                      
[19490.718608] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error                                                                                                      
[19490.718612] end_request: I/O error, dev sdd, sector 0                                                                                                                 
[19490.718619] Buffer I/O error on device sdd, logical block 0                                                                                                           
[19490.718627] Buffer I/O error on device sdd, logical block 1
[19490.718630] Buffer I/O error on device sdd, logical block 2
[19490.718633] Buffer I/O error on device sdd, logical block 3
[19502.526298] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[19502.526306] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]
[19502.526312] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error
[19502.526317] end_request: I/O error, dev sdd, sector 0
[19502.526322] Buffer I/O error on device sdd, logical block 0
[19514.372131] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[19514.372138] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]
[19514.372144] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error
[19514.372148] end_request: I/O error, dev sdd, sector 0
[19514.372153] Buffer I/O error on device sdd, logical block 0
[19514.372159] Buffer I/O error on device sdd, logical block 1
[19514.372162] Buffer I/O error on device sdd, logical block 2
[19514.372165] Buffer I/O error on device sdd, logical block 3
[19526.170208] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[19526.170216] sd 9:0:0:0: [sdd] Sense Key : Medium Error [current]
[19526.170220] sd 9:0:0:0: [sdd] Add. Sense: Unrecovered read error
[19526.170224] end_request: I/O error, dev sdd, sector 0
[19526.170229] Buffer I/O error on device sdd, logical block 0


First I hoped that mybe something is wrong with the controler of the HD case but i get the same error after putting the disk to some other case.

I read somewhere that the 'Sense Key : Medium Error [current]' might indicate a broken controler on the HD.

Thing is i would realy love to have a way to secure the data on the disk, and would be thankfull for any help and hints about what i can do to get that done ;)

thx

Calida

---

### Post by ddrichardson on 2009-03-19
> **Calida said:**
> I have a huge problem with one of my exteranal HD, a Wester Digital WD10EACS-00ZJB0

Since an hour ago it worked fine, i could read and write to and from it and now I get the following when I try to connect it to my PC:



First I hoped that mybe something is wrong with the controler of the HD case but i get the same error after putting the disk to some other case.

I read somewhere that the 'Sense Key : Medium Error [current]' might indicate a broken controler on the HD.

Thing is i would realy love to have a way to secure the data on the disk, and would be thankfull for any help and hints about what i can do to get that done ;)

thx

Calida
Is this a SMART capable drive and is it enabled in BIOS? Are there any SMART errors on boot and does BIOS still detect the device OK?

---

