---
title: "USB-Hard drive ADATA SH93 does not work."
date: 2010-04-02
forum: Hardware
---

### Post by veZuk on 2010-04-02
Good time of day.

I recently bought a USB hard drive ADATA SH93 640Gb ([http://adata.com.tw/en/product_show.php?ProductNo=14210001](http://adata.com.tw/en/product_show.php?ProductNo=14210001)), but no Karmic, nor Lucid did not want to work with him. One note - if you boot from the LiveCD Karmic (9.10) then it is visible and you can use it.

In addition, for example, ArchLinux, Ubuntu 8.04.1 on the same computer works fine with the disk.

I think  that's something wrong with the kernel.

When I connect the hard drive is in /var/log/syslog appear such messages:
> Apr  3 01:59:11 vezuk-etop kernel: [  239.990039] usb 2-4: new high speed USB device using ehci_hcd and address 4
Apr  3 01:59:12 vezuk-etop kernel: [  240.141636] usb 2-4: configuration #1 chosen from 1 choice
Apr  3 01:59:12 vezuk-etop kernel: [  240.141842] scsi3 : SCSI emulation for USB Mass Storage devices
Apr  3 01:59:12 vezuk-etop kernel: [  240.142020] usb-storage: device found at 4
Apr  3 01:59:12 vezuk-etop kernel: [  240.142023] usb-storage: waiting for device to settle before scanning
Apr  3 01:59:17 vezuk-etop kernel: [  245.140163] usb-storage: device scan complete
Apr  3 01:59:17 vezuk-etop kernel: [  245.140801] scsi 3:0:0:0: Direct-Access     A-DATA   SH93                  PQ: 0 ANSI: 0
Apr  3 01:59:17 vezuk-etop kernel: [  245.146075] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  3 01:59:17 vezuk-etop kernel: [  245.148794] sd 3:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Apr  3 01:59:17 vezuk-etop kernel: [  245.149292] sd 3:0:0:0: [sdc] Write Protect is off
Apr  3 01:59:17 vezuk-etop kernel: [  245.149296] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
Apr  3 01:59:17 vezuk-etop kernel: [  245.149300] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Apr  3 01:59:17 vezuk-etop kernel: [  245.151198] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Apr  3 01:59:17 vezuk-etop kernel: [  245.151208]  sdc: sdc1
Apr  3 01:59:17 vezuk-etop kernel: [  245.177867] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Apr  3 01:59:17 vezuk-etop kernel: [  245.177875] sd 3:0:0:0: [sdc] Attached SCSI disk
Apr  3 01:59:30 vezuk-etop kernel: [  258.972562] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.972570] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.972577] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.972585] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.972596] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.972603] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.973533] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.973541] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.973548] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.973554] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.973565] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.973572] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.974561] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.974567] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.974574] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.974580] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.974590] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.974595] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.975535] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.975543] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.975549] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.975556] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.975567] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.975573] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.976556] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.976562] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.976568] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.976574] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.976584] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.976589] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.977526] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.977533] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.977540] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.977547] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.977558] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.977564] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.978552] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.978558] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.978564] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.978570] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.978581] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.978585] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.979551] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.979557] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.979563] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.979568] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.979578] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.979582] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.980523] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.980529] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.980535] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.980541] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.980552] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.980557] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.981524] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.981534] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.981543] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.981553] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.981570] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.981578] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:30 vezuk-etop kernel: [  258.982534] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.982540] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.982547] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.982554] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 38 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.982564] end_request: I/O error, dev sdc, sector 2104
Apr  3 01:59:30 vezuk-etop kernel: [  258.983521] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.983527] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.983533] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.983540] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.983550] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:30 vezuk-etop kernel: [  258.984394] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:30 vezuk-etop kernel: [  258.984400] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:30 vezuk-etop kernel: [  258.984406] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:30 vezuk-etop kernel: [  258.984412] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:30 vezuk-etop kernel: [  258.984422] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:42 vezuk-etop kernel: [  270.146340] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:42 vezuk-etop kernel: [  270.146349] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:42 vezuk-etop kernel: [  270.146355] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:42 vezuk-etop kernel: [  270.146363] sd 3:0:0:0: [sdc] CDB: Read(10): 28 00 4a 85 77 80 00 00 08 00
Apr  3 01:59:42 vezuk-etop kernel: [  270.146377] end_request: I/O error, dev sdc, sector 1250260864
Apr  3 01:59:42 vezuk-etop kernel: [  270.146383] __ratelimit: 3 callbacks suppressed
Apr  3 01:59:42 vezuk-etop kernel: [  270.146388] Buffer I/O error on device sdc1, logical block 156282352
Apr  3 01:59:42 vezuk-etop kernel: [  270.147328] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:42 vezuk-etop kernel: [  270.147334] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:42 vezuk-etop kernel: [  270.147339] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:42 vezuk-etop kernel: [  270.147345] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 00 00 20 00
Apr  3 01:59:42 vezuk-etop kernel: [  270.147355] end_request: I/O error, dev sdc, sector 0
Apr  3 01:59:42 vezuk-etop kernel: [  270.147360] Buffer I/O error on device sdc, logical block 0
Apr  3 01:59:42 vezuk-etop kernel: [  270.147365] Buffer I/O error on device sdc, logical block 1
Apr  3 01:59:42 vezuk-etop kernel: [  270.147369] Buffer I/O error on device sdc, logical block 2
Apr  3 01:59:42 vezuk-etop kernel: [  270.147373] Buffer I/O error on device sdc, logical block 3
Apr  3 01:59:53 vezuk-etop kernel: [  281.309474] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:53 vezuk-etop kernel: [  281.309483] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:53 vezuk-etop kernel: [  281.309490] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:53 vezuk-etop kernel: [  281.309497] sd 3:0:0:0: [sdc] CDB: Read(10): 28 00 4a 85 77 f0 00 00 08 00
Apr  3 01:59:53 vezuk-etop kernel: [  281.309512] end_request: I/O error, dev sdc, sector 1250260976
Apr  3 01:59:53 vezuk-etop kernel: [  281.309520] Buffer I/O error on device sdc1, logical block 156282366
Apr  3 01:59:53 vezuk-etop kernel: [  281.310453] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:53 vezuk-etop kernel: [  281.310459] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:53 vezuk-etop kernel: [  281.310465] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:53 vezuk-etop kernel: [  281.310472] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 00 08 00
Apr  3 01:59:53 vezuk-etop kernel: [  281.310482] end_request: I/O error, dev sdc, sector 2048
Apr  3 01:59:53 vezuk-etop kernel: [  281.310488] Buffer I/O error on device sdc1, logical block 0
Apr  3 01:59:53 vezuk-etop kernel: [  281.311459] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 01:59:53 vezuk-etop kernel: [  281.311465] sd 3:0:0:0: [sdc] Sense Key : Illegal Request [current] 
Apr  3 01:59:53 vezuk-etop kernel: [  281.311470] sd 3:0:0:0: [sdc] Add. Sense: Invalid command operation code
Apr  3 01:59:53 vezuk-etop kernel: [  281.311477] sd 3:0:0:0: [sdc] CDB: Read(6): 08 00 08 08 08 00
Apr  3 01:59:53 vezuk-etop kernel: [  281.311486] end_request: I/O error, dev sdc, sector 2056
Apr  3 01:59:53 vezuk-etop kernel: [  281.311491] Buffer I/O error on device sdc1, logical block 1
...The disc is not broken, electronics works as expected.
> $ uname -a
Linux vezuk-etop 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
I'm not the only one who has a problem (In Russian: [http://old.nabble.com/USB-HDD-td27944884.html](http://old.nabble.com/USB-HDD-td27944884.html)).

Are there ways to solve this problem?

---

### Post by veZuk on 2010-04-05
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554283](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554283)

---

