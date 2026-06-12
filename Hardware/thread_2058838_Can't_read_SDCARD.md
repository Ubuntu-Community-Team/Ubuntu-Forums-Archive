---
title: "Can't read SDCARD"
date: 2012-09-16
forum: Hardware
---

### Post by grenier on 2012-09-16
(Ok, I'm trying that again, this time without the xubuntu tag.)

I have an internal sdcard reader on my desktop (plugged on one of the USB ports of the motherboard). I did a fresh install a couple of months ago and although it originally worked, it stopped doing so for a while now. The reader includes a number of formats, including a USB port, which works fine.

I've tested that reader with a number of other sdcards but it's a no go, when they all work fine with other computers (be them under windows or linux of the same flavor). Just to make sure, I digged out an external card reader, and it does the exact same thing.

I also checked whether it was a formatting problem with the disk tool, and saw that the computer sees that a card is present, but it doesn't recognize the file system (which is a very basic FAT formating, the cards are used in my camera).

Any idea ?

---

### Post by sanderj on 2012-09-16
I had the same a few days ago. I then discovered a lot of ugly message in /var/log/syslog or dmesg about all kinds of problems with the SD card.

So ... can you check your /var/log/syslog and dmesg?

---

### Post by grenier on 2012-09-21
Ok, here is what is added to /var/log/syslog within a few seconds of inserting the sdcard :
```
Sep 21 18:11:39 Nodachi kernel: [275400.717516] sd 6:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
Sep 21 18:11:39 Nodachi kernel: [275400.719134] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:39 Nodachi kernel: [275400.719137] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:39 Nodachi kernel: [275400.722136] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:39 Nodachi kernel: [275400.722139] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:39 Nodachi kernel: [275400.848044] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:40 Nodachi kernel: [275401.948750] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:40 Nodachi kernel: [275401.948754] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:40 Nodachi kernel: [275401.948757] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:40 Nodachi kernel: [275401.948760] Info fld=0x0
Sep 21 18:11:40 Nodachi kernel: [275401.948762] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:40 Nodachi kernel: [275401.948766] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:40 Nodachi kernel: [275401.948772] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:40 Nodachi kernel: [275401.948775] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:40 Nodachi kernel: [275401.948868] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:40 Nodachi kernel: [275401.948887] Dev sdb: unable to read RDB block 0
Sep 21 18:11:40 Nodachi kernel: [275401.948915]  sdb: unable to read partition table
Sep 21 18:11:40 Nodachi kernel: [275402.042150] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:40 Nodachi kernel: [275402.042155] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:40 Nodachi kernel: [275402.044394] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:40 Nodachi kernel: [275402.044399] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:40 Nodachi kernel: [275402.172072] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:41 Nodachi kernel: [275403.272623] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:41 Nodachi kernel: [275403.272627] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:41 Nodachi kernel: [275403.272630] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:41 Nodachi kernel: [275403.272633] Info fld=0x0
Sep 21 18:11:41 Nodachi kernel: [275403.272634] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:41 Nodachi kernel: [275403.272638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:41 Nodachi kernel: [275403.272643] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:41 Nodachi kernel: [275403.272646] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:41 Nodachi kernel: [275403.272721] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:41 Nodachi kernel: [275403.272737] Dev sdb: unable to read RDB block 0
Sep 21 18:11:41 Nodachi kernel: [275403.272764]  sdb: unable to read partition table
Sep 21 18:11:41 Nodachi kernel: [275403.277635] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:41 Nodachi kernel: [275403.277639] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:41 Nodachi kernel: [275403.279891] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:41 Nodachi kernel: [275403.279894] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:41 Nodachi kernel: [275403.400053] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:43 Nodachi kernel: [275404.500624] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:43 Nodachi kernel: [275404.500627] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:43 Nodachi kernel: [275404.500630] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:43 Nodachi kernel: [275404.500633] Info fld=0x0
Sep 21 18:11:43 Nodachi kernel: [275404.500634] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:43 Nodachi kernel: [275404.500638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:43 Nodachi kernel: [275404.500643] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:43 Nodachi kernel: [275404.500647] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:43 Nodachi kernel: [275404.500724] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:43 Nodachi kernel: [275404.500741] Dev sdb: unable to read RDB block 0
Sep 21 18:11:43 Nodachi kernel: [275404.500767]  sdb: unable to read partition table
Sep 21 18:11:43 Nodachi kernel: [275404.628052] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:44 Nodachi kernel: [275405.728750] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:44 Nodachi kernel: [275405.728753] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:44 Nodachi kernel: [275405.728756] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:44 Nodachi kernel: [275405.728759] Info fld=0x0
Sep 21 18:11:44 Nodachi kernel: [275405.728761] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:44 Nodachi kernel: [275405.728769] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Sep 21 18:11:44 Nodachi kernel: [275405.728777] end_request: I/O error, dev sdb, sector 8
Sep 21 18:11:44 Nodachi kernel: [275405.732024] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:44 Nodachi kernel: [275405.732029] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:44 Nodachi kernel: [275405.734635] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:44 Nodachi kernel: [275405.734638] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:44 Nodachi kernel: [275405.734687] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:44 Nodachi kernel: [275405.734702] Dev sdb: unable to read RDB block 0
Sep 21 18:11:44 Nodachi kernel: [275405.734723]  sdb: unable to read partition table
Sep 21 18:11:44 Nodachi kernel: [275405.739634] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:44 Nodachi kernel: [275405.739637] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:44 Nodachi kernel: [275405.742012] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:44 Nodachi kernel: [275405.742015] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:44 Nodachi kernel: [275405.872065] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:45 Nodachi kernel: [275406.972753] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:45 Nodachi kernel: [275406.972757] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:45 Nodachi kernel: [275406.972759] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:45 Nodachi kernel: [275406.972763] Info fld=0x0
Sep 21 18:11:45 Nodachi kernel: [275406.972764] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:45 Nodachi kernel: [275406.972768] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:45 Nodachi kernel: [275406.972773] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:45 Nodachi kernel: [275406.972777] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:45 Nodachi kernel: [275406.972920] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:45 Nodachi kernel: [275406.972940] Dev sdb: unable to read RDB block 0
Sep 21 18:11:45 Nodachi kernel: [275406.972971]  sdb: unable to read partition table
Sep 21 18:11:45 Nodachi kernel: [275406.977128] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:45 Nodachi kernel: [275406.977132] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:45 Nodachi kernel: [275406.979385] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:45 Nodachi kernel: [275406.979387] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:45 Nodachi kernel: [275407.108098] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:46 Nodachi kernel: [275408.212876] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:46 Nodachi kernel: [275408.212880] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:46 Nodachi kernel: [275408.212883] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:46 Nodachi kernel: [275408.212886] Info fld=0x0
Sep 21 18:11:46 Nodachi kernel: [275408.212887] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:46 Nodachi kernel: [275408.212891] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:46 Nodachi kernel: [275408.212896] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:46 Nodachi kernel: [275408.212900] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:46 Nodachi kernel: [275408.212989] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:46 Nodachi kernel: [275408.213006] Dev sdb: unable to read RDB block 0
Sep 21 18:11:46 Nodachi kernel: [275408.213033]  sdb: unable to read partition table
Sep 21 18:11:46 Nodachi kernel: [275408.216513] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:46 Nodachi kernel: [275408.216516] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:46 Nodachi kernel: [275408.218757] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:46 Nodachi kernel: [275408.218760] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:46 Nodachi kernel: [275408.340055] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:48 Nodachi kernel: [275409.440625] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:48 Nodachi kernel: [275409.440629] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:48 Nodachi kernel: [275409.440632] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:48 Nodachi kernel: [275409.440635] Info fld=0x0
Sep 21 18:11:48 Nodachi kernel: [275409.440636] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:48 Nodachi kernel: [275409.440640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:48 Nodachi kernel: [275409.440645] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:48 Nodachi kernel: [275409.440648] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:48 Nodachi kernel: [275409.440724] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:48 Nodachi kernel: [275409.440741] Dev sdb: unable to read RDB block 0
Sep 21 18:11:48 Nodachi kernel: [275409.440766]  sdb: unable to read partition table
Sep 21 18:11:48 Nodachi kernel: [275409.446263] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:48 Nodachi kernel: [275409.446267] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:48 Nodachi kernel: [275409.448519] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:48 Nodachi kernel: [275409.448522] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:48 Nodachi kernel: [275409.572059] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:49 Nodachi kernel: [275410.672626] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:49 Nodachi kernel: [275410.672629] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:49 Nodachi kernel: [275410.672632] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:49 Nodachi kernel: [275410.672635] Info fld=0x0
Sep 21 18:11:49 Nodachi kernel: [275410.672636] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:49 Nodachi kernel: [275410.672640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:49 Nodachi kernel: [275410.672645] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:49 Nodachi kernel: [275410.672648] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:49 Nodachi kernel: [275410.672751] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:49 Nodachi kernel: [275410.672771] Dev sdb: unable to read RDB block 0
Sep 21 18:11:49 Nodachi kernel: [275410.672801]  sdb: unable to read partition table
Sep 21 18:11:49 Nodachi kernel: [275410.676513] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:49 Nodachi kernel: [275410.676516] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:49 Nodachi kernel: [275410.678762] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:49 Nodachi kernel: [275410.678765] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:49 Nodachi kernel: [275410.800076] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:50 Nodachi kernel: [275411.900751] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:50 Nodachi kernel: [275411.900754] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:50 Nodachi kernel: [275411.900757] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:50 Nodachi kernel: [275411.900760] Info fld=0x0
Sep 21 18:11:50 Nodachi kernel: [275411.900761] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:50 Nodachi kernel: [275411.900765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:50 Nodachi kernel: [275411.900770] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:50 Nodachi kernel: [275411.900774] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:50 Nodachi kernel: [275411.900846] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:50 Nodachi kernel: [275411.900863] Dev sdb: unable to read RDB block 0
Sep 21 18:11:50 Nodachi kernel: [275411.900889]  sdb: unable to read partition table
Sep 21 18:11:50 Nodachi kernel: [275411.903646] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:50 Nodachi kernel: [275411.903649] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:50 Nodachi kernel: [275411.906017] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:50 Nodachi kernel: [275411.906020] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:50 Nodachi kernel: [275412.032048] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:51 Nodachi kernel: [275413.132626] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:51 Nodachi kernel: [275413.132629] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:51 Nodachi kernel: [275413.132632] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:51 Nodachi kernel: [275413.132635] Info fld=0x0
Sep 21 18:11:51 Nodachi kernel: [275413.132636] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:51 Nodachi kernel: [275413.132640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:51 Nodachi kernel: [275413.132645] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:51 Nodachi kernel: [275413.132649] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:51 Nodachi kernel: [275413.132731] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:51 Nodachi kernel: [275413.132747] Dev sdb: unable to read RDB block 0
Sep 21 18:11:51 Nodachi kernel: [275413.132773]  sdb: unable to read partition table
Sep 21 18:11:51 Nodachi kernel: [275413.138147] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:51 Nodachi kernel: [275413.138150] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:51 Nodachi kernel: [275413.140377] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:51 Nodachi kernel: [275413.140380] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:51 Nodachi kernel: [275413.264052] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:52 Nodachi kernel: [275414.364627] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:52 Nodachi kernel: [275414.364630] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:52 Nodachi kernel: [275414.364634] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:52 Nodachi kernel: [275414.364637] Info fld=0x0
Sep 21 18:11:52 Nodachi kernel: [275414.364638] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:52 Nodachi kernel: [275414.364642] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:52 Nodachi kernel: [275414.364646] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:52 Nodachi kernel: [275414.364650] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:52 Nodachi kernel: [275414.364727] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:52 Nodachi kernel: [275414.364743] Dev sdb: unable to read RDB block 0
Sep 21 18:11:52 Nodachi kernel: [275414.364768]  sdb: unable to read partition table
Sep 21 18:11:52 Nodachi kernel: [275414.368639] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:52 Nodachi kernel: [275414.368642] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:52 Nodachi kernel: [275414.371023] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:52 Nodachi kernel: [275414.371026] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:53 Nodachi kernel: [275414.492057] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:54 Nodachi kernel: [275415.596759] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:54 Nodachi kernel: [275415.596764] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:54 Nodachi kernel: [275415.596767] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:54 Nodachi kernel: [275415.596771] Info fld=0x0
Sep 21 18:11:54 Nodachi kernel: [275415.596772] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:54 Nodachi kernel: [275415.596777] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:54 Nodachi kernel: [275415.596783] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:54 Nodachi kernel: [275415.596787] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:54 Nodachi kernel: [275415.596921] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:54 Nodachi kernel: [275415.596942] Dev sdb: unable to read RDB block 0
Sep 21 18:11:54 Nodachi kernel: [275415.596977]  sdb: unable to read partition table
Sep 21 18:11:54 Nodachi kernel: [275415.600523] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:54 Nodachi kernel: [275415.600528] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:54 Nodachi kernel: [275415.603014] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:54 Nodachi kernel: [275415.603019] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:54 Nodachi kernel: [275415.724123] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
Sep 21 18:11:55 Nodachi kernel: [275416.824626] sd 6:0:0:0: [sdb] Media Changed
Sep 21 18:11:55 Nodachi kernel: [275416.824630] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 18:11:55 Nodachi kernel: [275416.824633] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
Sep 21 18:11:55 Nodachi kernel: [275416.824636] Info fld=0x0
Sep 21 18:11:55 Nodachi kernel: [275416.824637] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
Sep 21 18:11:55 Nodachi kernel: [275416.824641] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 18:11:55 Nodachi kernel: [275416.824646] end_request: I/O error, dev sdb, sector 0
Sep 21 18:11:55 Nodachi kernel: [275416.824650] Buffer I/O error on device sdb, logical block 0
Sep 21 18:11:55 Nodachi kernel: [275416.824718] ldm_validate_partition_table(): Disk read failed.
Sep 21 18:11:55 Nodachi kernel: [275416.824735] Dev sdb: unable to read RDB block 0
Sep 21 18:11:55 Nodachi kernel: [275416.824759]  sdb: unable to read partition table
Sep 21 18:11:55 Nodachi kernel: [275416.830265] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:55 Nodachi kernel: [275416.830268] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:55 Nodachi kernel: [275416.832640] sd 6:0:0:0: [sdb] No Caching mode page present
Sep 21 18:11:55 Nodachi kernel: [275416.832643] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 18:11:55 Nodachi kernel: [275416.960078] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
```

and here is what appears in dmesg :

```
[275656.524230] sdb: detected capacity change from 7948206080 to 0
[275738.525524] sd 6:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
[275738.527135] sd 6:0:0:0: [sdb] No Caching mode page present
[275738.527138] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275738.529388] sd 6:0:0:0: [sdb] No Caching mode page present
[275738.529391] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275738.652057] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
[275739.752755] sd 6:0:0:0: [sdb] Media Changed
[275739.752759] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[275739.752763] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
[275739.752766] Info fld=0x0
[275739.752768] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
[275739.752774] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[275739.752780] end_request: I/O error, dev sdb, sector 0
[275739.752784] quiet_error: 155 callbacks suppressed
[275739.752787] Buffer I/O error on device sdb, logical block 0
[275739.752883] ldm_validate_partition_table(): Disk read failed.
[275739.752904] Dev sdb: unable to read RDB block 0
[275739.752935]  sdb: unable to read partition table
[275739.760038] sd 6:0:0:0: [sdb] No Caching mode page present
[275739.760043] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275739.762391] sd 6:0:0:0: [sdb] No Caching mode page present
[275739.762395] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275739.888081] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
[275740.996750] sd 6:0:0:0: [sdb] Media Changed
[275740.996753] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[275740.996756] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
[275740.996759] Info fld=0x0
[275740.996760] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
[275740.996764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[275740.996769] end_request: I/O error, dev sdb, sector 0
[275740.996772] Buffer I/O error on device sdb, logical block 0
[275740.996838] ldm_validate_partition_table(): Disk read failed.
[275740.996854] Dev sdb: unable to read RDB block 0
[275740.996884]  sdb: unable to read partition table
[275741.000889] sd 6:0:0:0: [sdb] No Caching mode page present
[275741.000892] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275741.003389] sd 6:0:0:0: [sdb] No Caching mode page present
[275741.003391] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[275741.124060] usb 1-5: reset high-speed USB device number 4 using ehci_hcd
[275742.224750] sd 6:0:0:0: [sdb] Media Changed
[275742.224752] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[275742.224755] sd 6:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
[275742.224758] Info fld=0x0
[275742.224759] sd 6:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
[275742.224763] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[275742.224768] end_request: I/O error, dev sdb, sector 0
[275742.224772] Buffer I/O error on device sdb, logical block 0
[275742.224858] ldm_validate_partition_table(): Disk read failed.
[275742.224875] Dev sdb: unable to read RDB block 0
[275742.224902]  sdb: unable to read partition table
```

and so on, ad nauseum...

Originally (fresh install), the reader did work properly, so at some point, one update broke something.

---

### Post by irv on 2012-09-21
I thought I would just throw this out here. Awhile back I had an issue with a SD card so I ran gparted and switch to the SD card and checked it for errors and then ran a fix on it. After that I could read the card.

This might not have anything to do with your problem, but it would show if the card is OK or not.

---

### Post by grenier on 2012-09-21
Well, the card is ok, as I use it with my camera and I can use it just fine on another computer that runs an ubuntu 12.04 based linux (Bodhi 2.x)

---

### Post by gcbzzzz on 2012-10-12
I'm getting the same when using my beagleboard bone.

connect it via USB, all get this garbage over and over dmesg.

remove the microSD card, put into my lexar reader, it reads perfectly. pass all chkfs tests. i reimage it and same thing happens.

the board boots up and i can access it via ssh just fine. but USB mass storage is like that for me.

on the dmesg for the board, i get this over and over
`gadget: full-speed config #1: Linux File-Backed Storage`

still have to test the board on another computer. but the microsd card is definitely fine.

also, i'musing the same usb cable for the board and for the lexar, so i don't think it's it.

---

### Post by grenier on 2012-10-18
Well, I just can't read sdcards, period.
Although I can access any usb drive with no problem, even with an external usb card reader any sdcard simply is a no go.

I just don't get it.

---

