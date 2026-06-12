---
title: "Usb device not writable"
date: 2009-03-05
forum: Hardware
---

### Post by _exn_ on 2009-03-05
Hello.

 My distro 8.04lts , and i have a big, very big problem with usb device - mp3 player. 

 info:

   lsusb 
 ```

  Bus 001 Device 004: ID 10d6:1101 Actions Semiconductor Co., Ltd
 
```

  dmesg after connecting the device to usb port
 ```

[ 9578.086741] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 9578.220957] usb 1-5: configuration #1 chosen from 1 choice
[ 9578.221211] scsi10 : SCSI emulation for USB Mass Storage devices
[ 9578.221414] usb-storage: device found at 4
[ 9578.221416] usb-storage: waiting for device to settle before scanning
[ 9583.218533] usb-storage: device scan complete
[ 9583.219890] scsi scan: INQUIRY result too short (5), using 36
[ 9583.219894] scsi 10:0:0:0: Direct-Access     GENERIC  USB DISK DEVICE  1.00 PQ: 0 ANSI: 0 CCS
[ 9583.221705] sd 10:0:0:0: [sdb] 15950530 512-byte hardware sectors (8167 MB)
[ 9583.223836] sd 10:0:0:0: [sdb] Write Protect is off
[ 9583.223840] sd 10:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 9583.223842] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 9583.230704] sd 10:0:0:0: [sdb] 15950530 512-byte hardware sectors (8167 MB)
[ 9583.232714] sd 10:0:0:0: [sdb] Write Protect is off
[ 9583.232718] sd 10:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 9583.232720] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 9583.232723]  sdb: sdb1
[ 9583.235087]  sdb: p1 exceeds device capacity
[ 9583.302260] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 9583.302295] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 9583.432757] attempt to access beyond end of device
[ 9583.432764] sdb: rw=0, want=15950576, limit=15950530
[ 9583.432768] Buffer I/O error on device sdb1, logical block 15950512
[ 9583.432771] attempt to access beyond end of device
[ 9583.432772] sdb: rw=0, want=15950577, limit=15950530
[ 9583.432774] Buffer I/O error on device sdb1, logical block 15950513
[ 9583.432776] attempt to access beyond end of device
[ 9583.432777] sdb: rw=0, want=15950578, limit=15950530
[ 9583.432779] Buffer I/O error on device sdb1, logical block 15950514
[ 9583.432781] attempt to access beyond end of device
[ 9583.432783] sdb: rw=0, want=15950579, limit=15950530
[ 9583.432785] Buffer I/O error on device sdb1, logical block 15950515
[ 9583.432788] attempt to access beyond end of device
[ 9583.432790] sdb: rw=0, want=15950580, limit=15950530
[ 9583.432792] Buffer I/O error on device sdb1, logical block 15950516
[ 9583.432794] attempt to access beyond end of device
[ 9583.432796] sdb: rw=0, want=15950581, limit=15950530
[ 9583.432798] Buffer I/O error on device sdb1, logical block 15950517
[ 9583.432800] attempt to access beyond end of device
[ 9583.432802] sdb: rw=0, want=15950582, limit=15950530
[ 9583.432804] Buffer I/O error on device sdb1, logical block 15950518
[ 9583.432806] attempt to access beyond end of device
[ 9583.432808] sdb: rw=0, want=15950583, limit=15950530
[ 9583.432810] Buffer I/O error on device sdb1, logical block 15950519
[ 9583.432813] attempt to access beyond end of device
[ 9583.432815] sdb: rw=0, want=15950576, limit=15950530
[ 9583.432817] Buffer I/O error on device sdb1, logical block 15950512
[ 9583.432819] attempt to access beyond end of device

[ 9583.432836] sdb: rw=0, want=15950580, limit=15950530
[ 9583.432838] attempt to access beyond end of device
[ 9583.432840] sdb: rw=0, want=15950581, limit=15950530
[ 9583.432842] attempt to access beyond end of device
[ 9583.432843] sdb: rw=0, want=15950582, limit=15950530
[ 9583.432845] attempt to access beyond end of device
[ 9583.432847] sdb: rw=0, want=15950583, limit=15950530
[ 9583.432935] attempt to access beyond end of device
[ 9583.432937] sdb: rw=0, want=15950592, limit=15950530
[ 9583.432940] attempt to access beyond end of device
[ 9583.432942] sdb: rw=0, want=15950592, limit=15950530
[ 9583.432950] attempt to access beyond end of device
[ 9583.432952] sdb: rw=0, want=15950584, limit=15950530
[ 9583.432954] attempt to access beyond end of device
[ 9583.432956] sdb: rw=0, want=15950585, limit=15950530
[ 9583.432958] attempt to access beyond end of device
[ 9583.432960] sdb: rw=0, want=15950586, limit=15950530
[ 9583.432963] attempt to access beyond end of device
[ 9583.432965] sdb: rw=0, want=15950587, limit=15950530
[ 9583.432967] attempt to access beyond end of device
[ 9583.432969] sdb: rw=0, want=15950588, limit=15950530
[ 9583.432972] attempt to access beyond end of device
[ 9583.432974] sdb: rw=0, want=15950589, limit=15950530
[ 9583.432976] attempt to access beyond end of device
[ 9583.432978] sdb: rw=0, want=15950590, limit=15950530
[ 9583.432980] attempt to access beyond end of device
[ 9583.432982] sdb: rw=0, want=15950591, limit=15950530
[ 9583.432985] attempt to access beyond end of device
[ 9583.432987] sdb: rw=0, want=15950584, limit=15950530
[ 9583.432990] attempt to access beyond end of device
[ 9583.432992] sdb: rw=0, want=15950585, limit=15950530
[ 9583.432994] attempt to access beyond end of device
[ 9583.432996] sdb: rw=0, want=15950586, limit=15950530
[ 9583.432998] attempt to access beyond end of device
[ 9583.433000] sdb: rw=0, want=15950587, limit=15950530
[ 9583.433003] attempt to access beyond end of device
[ 9583.433005] sdb: rw=0, want=15950588, limit=15950530
[ 9583.433007] attempt to access beyond end of device
[ 9583.433009] sdb: rw=0, want=15950589, limit=15950530
[ 9583.433011] attempt to access beyond end of device
[ 9583.433013] sdb: rw=0, want=15950590, limit=15950530
[ 9583.433015] attempt to access beyond end of device
[ 9583.433018] sdb: rw=0, want=15950591, limit=15950530
[ 9583.433022] attempt to access beyond end of device
[ 9583.433024] sdb: rw=0, want=15950592, limit=15950530
[ 9583.433029] attempt to access beyond end of device
[ 9583.433031] sdb: rw=0, want=15950592, limit=15950530
[ 9583.433035] attempt to access beyond end of device
[ 9583.433038] sdb: rw=0, want=15950592, limit=15950530
[ 9583.433042] attempt to access beyond end of device
[ 9583.433045] sdb: rw=0, want=15950584, limit=15950530
[ 9583.433047] attempt to access beyond end of device
[ 9583.433049] sdb: rw=0, want=15950585, limit=15950530
[ 9583.433051] attempt to access beyond end of device
[ 9583.433053] sdb: rw=0, want=15950586, limit=15950530
[ 9583.433056] attempt to access beyond end of device
[ 9583.433058] sdb: rw=0, want=15950587, limit=15950530
[ 9583.433060] attempt to access beyond end of device
[ 9583.433062] sdb: rw=0, want=15950588, limit=15950530
[ 9583.433064] attempt to access beyond end of device
[ 9583.433066] sdb: rw=0, want=15950589, limit=15950530
[ 9583.433069] attempt to access beyond end of device
[ 9583.433071] sdb: rw=0, want=15950590, limit=15950530
[ 9583.433073] attempt to access beyond end of device
[ 9583.433075] sdb: rw=0, want=15950591, limit=15950530
[ 9583.433085] attempt to access beyond end of device
[ 9583.433087] sdb: rw=0, want=15950531, limit=15950530
[ 9583.433089] attempt to access beyond end of device
[ 9583.433091] sdb: rw=0, want=15950532, limit=15950530
[ 9583.433093] attempt to access beyond end of device
[ 9583.433095] sdb: rw=0, want=15950533, limit=15950530
[ 9583.433097] attempt to access beyond end of device
[ 9583.433099] sdb: rw=0, want=15950534, limit=15950530
[ 9583.433102] attempt to access beyond end of device
[ 9583.433104] sdb: rw=0, want=15950535, limit=15950530
[ 9583.444635] attempt to access beyond end of device
[ 9583.444640] sdb: rw=0, want=15950576, limit=15950530
[ 9583.444643] attempt to access beyond end of device
[ 9583.444645] sdb: rw=0, want=15950577, limit=15950530
[ 9583.444646] attempt to access beyond end of device
[ 9583.444648] sdb: rw=0, want=15950578, limit=15950530
[ 9583.444649] attempt to access beyond end of device
[ 9583.444650] sdb: rw=0, want=15950579, limit=15950530
[ 9583.444652] attempt to access beyond end of device
[ 9583.444654] sdb: rw=0, want=15950580, limit=15950530
[ 9583.444656] attempt to access beyond end of device
[ 9583.444658] sdb: rw=0, want=15950581, limit=15950530
[ 9583.444660] attempt to access beyond end of device
[ 9583.444662] sdb: rw=0, want=15950582, limit=15950530
[ 9583.444664] attempt to access beyond end of device
[ 9583.444666] sdb: rw=0, want=15950583, limit=15950530
[ 9583.444671] attempt to access beyond end of device
[ 9583.444673] sdb: rw=0, want=15950592, limit=15950530
[ 9583.444678] attempt to access beyond end of device
[ 9583.444680] sdb: rw=0, want=15950592, limit=15950530
 
```

After mounting , just mounting without any options i can see content of this flash drive, but if i change anything, or upload any file to that - this files don't readable after umounting and mounting again. Also i try to mount this with "sync" option, and this works, but speed for upload = 0-16kb. This is veeery slow for 8gb device.


 Any ideas ?

---

### Post by _exn_ on 2009-03-05
On the laptop (8.04lts too) everything looks exactly the same.

 But in windows this works fine, but i not have windows :(

---

