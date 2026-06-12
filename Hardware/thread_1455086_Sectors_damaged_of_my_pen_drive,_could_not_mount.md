---
title: "Sectors damaged of my pen drive, could not mount"
date: 2010-04-15
forum: Hardware
---

### Post by _cvt_ on 2010-04-15
Hi,
   I'm searching for a solution 2 days. Other day during coping some archives in the Windows Vista (****!) occurred an error and now I'm trying to get up my pen drive.

Na verdade não é um pen drive mas um micro sd com adaptador usb.

Here is the dmesg when I plug it:
> [  227.112016] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  227.255521] usb 1-5: configuration #1 chosen from 1 choice
[  227.256849] scsi10 : SCSI emulation for USB Mass Storage devices
[  227.256958] usb-storage: device found at 5
[  227.256960] usb-storage: waiting for device to settle before scanning
[  232.256440] usb-storage: device scan complete
[  232.257314] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9407 PQ: 0 ANSI: 0
[  232.257712] sd 10:0:0:0: Attached scsi generic sg6 type 0
[  232.405036] sd 10:0:0:0: [sdf] 15954944 512-byte logical blocks: (8.16 GB/7.60 GiB)
[  232.406156] sd 10:0:0:0: [sdf] Write Protect is off
[  232.406159] sd 10:0:0:0: [sdf] Mode Sense: 03 00 00 00
[  232.406162] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[  232.409408] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[  232.409412]  sdf: sdf1
[  232.412791] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[  232.412794] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[  236.757449] sd 10:0:0:0: [sdf] Device not ready
[  236.757453] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.757457] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.757461] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.757467] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.757476] end_request: I/O error, dev sdf, sector 56
[  236.757481] Buffer I/O error on device sdf, logical block 7
[  236.758821] sd 10:0:0:0: [sdf] Device not ready
[  236.758823] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.758826] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.758830] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.758835] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.758843] end_request: I/O error, dev sdf, sector 56
[  236.758846] Buffer I/O error on device sdf, logical block 7
[  236.760202] sd 10:0:0:0: [sdf] Device not ready
[  236.760205] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.760208] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.760212] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.760216] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.760226] end_request: I/O error, dev sdf, sector 56
[  236.760229] Buffer I/O error on device sdf, logical block 7
[  236.761697] sd 10:0:0:0: [sdf] Device not ready
[  236.761700] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.761703] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.761707] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.761711] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.761720] end_request: I/O error, dev sdf, sector 56
[  236.761723] Buffer I/O error on device sdf, logical block 7
[  236.763071] sd 10:0:0:0: [sdf] Device not ready
[  236.763073] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.763076] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.763080] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.763084] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.763093] end_request: I/O error, dev sdf, sector 56
[  236.763095] Buffer I/O error on device sdf, logical block 7
[  236.764453] sd 10:0:0:0: [sdf] Device not ready
[  236.764455] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.764458] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.764462] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.764467] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.764476] end_request: I/O error, dev sdf, sector 120
[  236.764479] Buffer I/O error on device sdf, logical block 15
[  236.765821] sd 10:0:0:0: [sdf] Device not ready
[  236.765823] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.765826] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.765830] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.765834] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.765843] end_request: I/O error, dev sdf, sector 120
[  236.765846] Buffer I/O error on device sdf, logical block 15
[  236.767195] sd 10:0:0:0: [sdf] Device not ready
[  236.767197] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.767200] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.767204] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.767208] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.767217] end_request: I/O error, dev sdf, sector 120
[  236.767219] Buffer I/O error on device sdf, logical block 15
[  236.768573] sd 10:0:0:0: [sdf] Device not ready
[  236.768576] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.768579] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.768583] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.768588] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.768596] end_request: I/O error, dev sdf, sector 120
[  236.768599] Buffer I/O error on device sdf, logical block 15
[  236.769946] sd 10:0:0:0: [sdf] Device not ready
[  236.769949] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.769952] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.769956] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.769960] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.769969] end_request: I/O error, dev sdf, sector 56
[  236.769972] Buffer I/O error on device sdf, logical block 7
[  236.771320] sd 10:0:0:0: [sdf] Device not ready
[  236.771322] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.771325] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.771329] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.771333] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  236.771342] end_request: I/O error, dev sdf, sector 56
[  236.772822] sd 10:0:0:0: [sdf] Device not ready
[  236.772824] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.772827] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.772831] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.772835] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.772844] end_request: I/O error, dev sdf, sector 120
[  236.774195] sd 10:0:0:0: [sdf] Device not ready
[  236.774197] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.774200] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.774204] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.774208] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  236.774216] end_request: I/O error, dev sdf, sector 120
[  236.775696] sd 10:0:0:0: [sdf] Device not ready
[  236.775699] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.775702] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.775706] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.775710] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.775719] end_request: I/O error, dev sdf, sector 16
[  236.777196] sd 10:0:0:0: [sdf] Device not ready
[  236.777198] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.777201] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.777205] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.777209] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.777218] end_request: I/O error, dev sdf, sector 128
[  236.778571] sd 10:0:0:0: [sdf] Device not ready
[  236.778573] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.778576] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.778580] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.778584] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.778593] end_request: I/O error, dev sdf, sector 128
[  236.779944] sd 10:0:0:0: [sdf] Device not ready
[  236.779946] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.779949] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.779953] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.779957] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.779966] end_request: I/O error, dev sdf, sector 128
[  236.781445] sd 10:0:0:0: [sdf] Device not ready
[  236.781447] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.781450] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.781454] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.781458] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.781467] end_request: I/O error, dev sdf, sector 16
[  236.782944] sd 10:0:0:0: [sdf] Device not ready
[  236.782946] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.782949] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.782953] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.782957] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.782966] end_request: I/O error, dev sdf, sector 128
[  236.784446] sd 10:0:0:0: [sdf] Device not ready
[  236.784449] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.784452] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.784456] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.784460] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.784469] end_request: I/O error, dev sdf, sector 64
[  236.786069] sd 10:0:0:0: [sdf] Device not ready
[  236.786071] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.786074] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.786078] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.786082] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.786091] end_request: I/O error, dev sdf, sector 64
[  236.787571] sd 10:0:0:0: [sdf] Device not ready
[  236.787573] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.787576] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.787580] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.787584] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.787593] end_request: I/O error, dev sdf, sector 64
[  236.788946] sd 10:0:0:0: [sdf] Device not ready
[  236.788948] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.788951] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.788955] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.788959] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.788968] end_request: I/O error, dev sdf, sector 64
[  236.790319] sd 10:0:0:0: [sdf] Device not ready
[  236.790321] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.790324] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.790327] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.790332] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.790340] end_request: I/O error, dev sdf, sector 64
[  236.791820] sd 10:0:0:0: [sdf] Device not ready
[  236.791822] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.791826] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.791830] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.791834] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.791843] end_request: I/O error, dev sdf, sector 64
[  236.793320] sd 10:0:0:0: [sdf] Device not ready
[  236.793322] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.793325] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.793329] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.793333] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.793342] end_request: I/O error, dev sdf, sector 64
[  236.794818] sd 10:0:0:0: [sdf] Device not ready
[  236.794820] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.794823] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.794827] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.794831] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.794840] end_request: I/O error, dev sdf, sector 64
[  236.796195] sd 10:0:0:0: [sdf] Device not ready
[  236.796197] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.796200] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.796204] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.796208] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.796217] end_request: I/O error, dev sdf, sector 64
[  236.797569] sd 10:0:0:0: [sdf] Device not ready
[  236.797571] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.797574] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.797578] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.797582] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  236.797591] end_request: I/O error, dev sdf, sector 64
[  236.798943] sd 10:0:0:0: [sdf] Device not ready
[  236.798945] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.798948] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.798952] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.798956] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[  236.798965] end_request: I/O error, dev sdf, sector 256
[  236.800447] sd 10:0:0:0: [sdf] Device not ready
[  236.800450] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.800454] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.800458] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.800462] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[  236.800471] end_request: I/O error, dev sdf, sector 256
[  236.801944] sd 10:0:0:0: [sdf] Device not ready
[  236.801947] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.801950] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.801954] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.801958] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[  236.801967] end_request: I/O error, dev sdf, sector 264
[  236.803317] sd 10:0:0:0: [sdf] Device not ready
[  236.803320] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.803323] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.803326] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.803331] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[  236.803339] end_request: I/O error, dev sdf, sector 264
[  236.804694] sd 10:0:0:0: [sdf] Device not ready
[  236.804696] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.804699] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.804703] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.804707] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[  236.804716] end_request: I/O error, dev sdf, sector 272
[  236.806069] sd 10:0:0:0: [sdf] Device not ready
[  236.806071] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.806074] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.806078] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.806082] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[  236.806091] end_request: I/O error, dev sdf, sector 272
[  236.807567] sd 10:0:0:0: [sdf] Device not ready
[  236.807569] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.807572] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.807576] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.807580] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[  236.807589] end_request: I/O error, dev sdf, sector 768
[  236.808944] sd 10:0:0:0: [sdf] Device not ready
[  236.808946] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.808949] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.808953] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.808957] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[  236.808966] end_request: I/O error, dev sdf, sector 768
[  236.810442] sd 10:0:0:0: [sdf] Device not ready
[  236.810444] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.810447] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.810451] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.810455] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[  236.810464] end_request: I/O error, dev sdf, sector 776
[  236.811817] sd 10:0:0:0: [sdf] Device not ready
[  236.811819] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.811822] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.811825] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.811830] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[  236.811838] end_request: I/O error, dev sdf, sector 776
[  236.813192] sd 10:0:0:0: [sdf] Device not ready
[  236.813194] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.813197] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.813201] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.813205] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[  236.813214] end_request: I/O error, dev sdf, sector 784
[  236.814692] sd 10:0:0:0: [sdf] Device not ready
[  236.814694] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.814697] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.814701] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.814705] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[  236.814713] end_request: I/O error, dev sdf, sector 784
[  236.816071] sd 10:0:0:0: [sdf] Device not ready
[  236.816074] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.816077] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.816081] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.816085] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.816094] end_request: I/O error, dev sdf, sector 16
[  236.817443] sd 10:0:0:0: [sdf] Device not ready
[  236.817446] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.817450] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.817454] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.817458] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.817467] end_request: I/O error, dev sdf, sector 16
[  236.818816] sd 10:0:0:0: [sdf] Device not ready
[  236.818819] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.818822] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.818825] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.818830] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.818838] end_request: I/O error, dev sdf, sector 16
[  236.820193] sd 10:0:0:0: [sdf] Device not ready
[  236.820196] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.820199] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.820203] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.820207] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.820216] end_request: I/O error, dev sdf, sector 128
[  236.821566] sd 10:0:0:0: [sdf] Device not ready
[  236.821568] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.821571] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.821575] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.821579] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.821588] end_request: I/O error, dev sdf, sector 128
[  236.822941] sd 10:0:0:0: [sdf] Device not ready
[  236.822943] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.822946] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.822950] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.822954] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.822962] end_request: I/O error, dev sdf, sector 16
[  236.824445] sd 10:0:0:0: [sdf] Device not ready
[  236.824448] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.824451] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.824455] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.824460] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  236.824469] end_request: I/O error, dev sdf, sector 16
[  236.825943] sd 10:0:0:0: [sdf] Device not ready
[  236.825945] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.825949] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.825953] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.825957] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  236.825966] end_request: I/O error, dev sdf, sector 128
[  236.827316] sd 10:0:0:0: [sdf] Device not ready
[  236.827318] sd 10:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  236.827321] sd 10:0:0:0: [sdf] Sense Key : Not Ready [current] 
[  236.827325] sd 10:0:0:0: [sdf] Add. Sense: Medium not present
[  236.827329] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[  236.827338] end_request: I/O error, dev sdf, sector 4096


I tryed many things like: gparted, mkfs,... but didn't work.

When i type:

[LIST]
[*]$ sudo mount /dev/sdf /media/pen/
> mount: /dev/sdf: unknown device
[*]$ sudo fdisk -l
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9eb4f9b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102400000    7  HPFS/NTFS
/dev/sda2   *       12749       19123    51200000   83  Linux
/dev/sda3           19123       19250     1024000   82  Linux swap / Solaris
/dev/sda4           19251       45145   207998976+   5  Extended
/dev/sda5           19251       31700    99998720   83  Linux
/dev/sda6           31700       44149    99998720   83  Linux
/dev/sda7           44149       45145     7999488   82  Linux swap / Solaris
[*]lsusb    (it is the SanDisk)
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 13ee:0003  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0781:b7b1 SanDisk Corp. 
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/LIST]

Could somebody help me ?

---

