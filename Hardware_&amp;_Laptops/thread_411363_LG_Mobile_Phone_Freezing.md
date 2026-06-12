---
title: "LG Mobile Phone Freezing"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by Tiago Cruz on 2007-04-16
Hello guys,

I have one LG Mobile Phone called Black Safira (MG810):
[http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=0000060102&parentCategoryId=0000000601&categoryLevel=4&productId=1100000411](http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=0000060102&parentCategoryId=0000000601&categoryLevel=4&productId=1100000411)

He works as well on Windows, but freeze on Ubuntu Feisty when I try use the USB cable to transfer some file.

Some dmesg:

```
[452939.774683] scsi 7:0:0:0: rejecting I/O to dead device
[452939.774688] sdb: Write Protect is off
[452939.774690] sdb: Mode Sense: 00 00 00 00
[452939.774692] sdb: assuming drive cache: write through
[452939.777708] scsi 7:0:0:0: rejecting I/O to dead device
[452939.777893] scsi 7:0:0:0: rejecting I/O to dead device
[452939.777987] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778081] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778175] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778268] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778366] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778459] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778572] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778665] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778758] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778851] scsi 7:0:0:0: rejecting I/O to dead device
[452939.778943] scsi 7:0:0:0: rejecting I/O to dead device
[452939.779036] scsi 7:0:0:0: rejecting I/O to dead device
[452939.779129] scsi 7:0:0:0: rejecting I/O to dead device
[452939.779222] scsi 7:0:0:0: rejecting I/O to dead device
[452939.795285] /dev/vmmon[11463]: host clock rate change request 19 -> 0
[452939.797710] scsi 7:0:0:0: rejecting I/O to dead device
[452939.799358] vmmon: Had to deallocate locked 15432 pages from vm driver e2a22000
[452939.802208] vmmon: Had to deallocate AWE 3305 pages from vm driver e2a22000
[452939.881551] usb 5-2: new full speed USB device using uhci_hcd and address 9
[452939.900777] scsi 7:0:0:0: rejecting I/O to dead device
[452939.901048] FAT: unable to read inode block for updating (i_pos 8445)
[452939.901573] scsi 7:0:0:0: rejecting I/O to dead device
[452939.901782] FAT: unable to read inode block for updating (i_pos 8500)
[452939.903730] scsi 7:0:0:0: rejecting I/O to dead device
[452943.056071] usb 5-2: device descriptor read/64, error -110
[452958.257886] usb 5-2: device descriptor read/64, error -110
[452958.473502] usb 5-2: new full speed USB device using uhci_hcd and address 10
[452961.592124] usb 5-2: device descriptor read/64, error -110
[452976.793920] usb 5-2: device descriptor read/64, error -110
[452977.009553] usb 5-2: new full speed USB device using uhci_hcd and address 11
[452982.025922] usb 5-2: device descriptor read/8, error -110
[452987.141105] usb 5-2: device descriptor read/8, error -110
[452987.359719] usb 5-2: new full speed USB device using uhci_hcd and address 12
[452992.376081] usb 5-2: device descriptor read/8, error -110
[452997.491265] usb 5-2: device descriptor read/8, error -110
```

kernel.log:

```
Apr 16 21:08:08 tuxkiller kernel: [452939.761794] usb 5-2: USB disconnect, address 8
Apr 16 21:08:08 tuxkiller kernel: [452939.761922] sd 7:0:0:0: scsi: Device offlined - not ready after error recovery
Apr 16 21:08:08 tuxkiller kernel: [452939.765750] sd 7:0:0:0: SCSI error: return code = 0x00010000
Apr 16 21:08:08 tuxkiller kernel: [452939.765755] end_request: I/O error, dev sdb, sector 56303
Apr 16 21:08:08 tuxkiller kernel: [452939.765787] printk: 60 messages suppressed.
Apr 16 21:08:08 tuxkiller kernel: [452939.765791] Buffer I/O error on device sdb, logical block 531
Apr 16 21:08:08 tuxkiller kernel: [452939.765795] lost page write due to I/O error on sdb
Apr 16 21:08:08 tuxkiller kernel: [452939.765801] Buffer I/O error on device sdb, logical block 533
Apr 16 21:08:08 tuxkiller kernel: [452939.765803] lost page write due to I/O error on sdb
Apr 16 21:08:08 tuxkiller kernel: [452939.765807] Buffer I/O error on device sdb, logical block 534
Apr 16 21:08:08 tuxkiller kernel: [452939.765809] lost page write due to I/O error on sdb
Apr 16 21:08:08 tuxkiller kernel: [452939.765817] Buffer I/O error on device sdb, logical block 34237
Apr 16 21:08:08 tuxkiller kernel: [452939.765819] lost page write due to I/O error on sdb
Apr 16 21:08:08 tuxkiller kernel: [452939.765823] Buffer I/O error on device sdb, logical block 34238
Apr 16 21:08:08 tuxkiller kernel: [452939.765825] lost page write due to I/O error on sdb
Apr 16 21:08:08 tuxkiller kernel: [452939.765833] Buffer I/O error on device sdb, logical block 63171
Apr 16 21:08:08 tuxkiller kernel: [452939.765837] Buffer I/O error on device sdb, logical block 63172
Apr 16 21:08:08 tuxkiller kernel: [452939.765842] Buffer I/O error on device sdb, logical block 63173
Apr 16 21:08:08 tuxkiller kernel: [452939.765845] Buffer I/O error on device sdb, logical block 63174
Apr 16 21:08:08 tuxkiller kernel: [452939.765850] Buffer I/O error on device sdb, logical block 63179
Apr 16 21:08:08 tuxkiller kernel: [452939.774372] VFS: busy inodes on changed media.
Apr 16 21:08:08 tuxkiller kernel: [452939.774475] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.774571] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.774662] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.774669] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.774674] sdb : READ CAPACITY failed.
Apr 16 21:08:08 tuxkiller kernel: [452939.774676] sdb : status=0, message=00, host=1, driver=00 
Apr 16 21:08:08 tuxkiller kernel: [452939.774679] sdb : sense not available. 
Apr 16 21:08:08 tuxkiller kernel: [452939.774683] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.774688] sdb: Write Protect is off
Apr 16 21:08:08 tuxkiller kernel: [452939.774690] sdb: Mode Sense: 00 00 00 00
Apr 16 21:08:08 tuxkiller kernel: [452939.774692] sdb: assuming drive cache: write through
Apr 16 21:08:08 tuxkiller kernel: [452939.777708] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.777893] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.777987] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778081] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778175] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778268] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778366] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778459] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778572] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778665] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778758] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778851] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.778943] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.779036] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.779129] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.779222] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.795285] /dev/vmmon[11463]: host clock rate change request 19 -> 0
Apr 16 21:08:08 tuxkiller kernel: [452939.797710] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.799358] vmmon: Had to deallocate locked 15432 pages from vm driver e2a22000
Apr 16 21:08:08 tuxkiller kernel: [452939.802208] vmmon: Had to deallocate AWE 3305 pages from vm driver e2a22000
Apr 16 21:08:08 tuxkiller kernel: [452939.881551] usb 5-2: new full speed USB device using uhci_hcd and address 9
Apr 16 21:08:08 tuxkiller kernel: [452939.900777] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.901048] FAT: unable to read inode block for updating (i_pos 8445)
Apr 16 21:08:08 tuxkiller kernel: [452939.901573] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:08 tuxkiller kernel: [452939.901782] FAT: unable to read inode block for updating (i_pos 8500)
Apr 16 21:08:08 tuxkiller kernel: [452939.903730] scsi 7:0:0:0: rejecting I/O to dead device
Apr 16 21:08:11 tuxkiller kernel: [452943.056071] usb 5-2: device descriptor read/64, error -110
Apr 16 21:08:26 tuxkiller kernel: [452958.257886] usb 5-2: device descriptor read/64, error -110
Apr 16 21:08:27 tuxkiller kernel: [452958.473502] usb 5-2: new full speed USB device using uhci_hcd and address 10
Apr 16 21:08:30 tuxkiller kernel: [452961.592124] usb 5-2: device descriptor read/64, error -110
Apr 16 21:08:45 tuxkiller kernel: [452976.793920] usb 5-2: device descriptor read/64, error -110
Apr 16 21:08:45 tuxkiller kernel: [452977.009553] usb 5-2: new full speed USB device using uhci_hcd and address 11
Apr 16 21:08:50 tuxkiller kernel: [452982.025922] usb 5-2: device descriptor read/8, error -110
Apr 16 21:08:55 tuxkiller kernel: [452987.141105] usb 5-2: device descriptor read/8, error -110
Apr 16 21:08:56 tuxkiller kernel: [452987.359719] usb 5-2: new full speed USB device using uhci_hcd and address 12
Apr 16 21:09:01 tuxkiller kernel: [452992.376081] usb 5-2: device descriptor read/8, error -110
Apr 16 21:09:06 tuxkiller kernel: [452997.491265] usb 5-2: device descriptor read/8, error -110
```

Can someone help me? 

Thanks
:guitar:

---

