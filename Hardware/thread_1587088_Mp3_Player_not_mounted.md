---
title: "Mp3 Player not mounted"
date: 2010-10-02
forum: Hardware
---

### Post by vfontanela on 2010-10-02
I have a mp3 player that can't be mounted in my computer when I'm running Linux. It works ok on Windows

I entered lsusb at the terminal and here it is:
Bus 004 Device 002: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player / AK1025 MP3/MP4 Player

Then dmesg:

```
[  149.655597] USB Mass Storage support registered.
[  149.663848] usb-storage: device found at 4
[  149.663852] usb-storage: waiting for device to settle before scanning
[  154.660255] usb-storage: device scan complete
[  154.661119] scsi 4:0:0:0: Direct-Access     ACTIONS  HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
[  154.663864] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  154.664971] sd 4:0:0:0: [sdb] 8354737 512-byte logical blocks: (4.27 GB/3.98 GiB)
[  154.665589] sd 4:0:0:0: [sdb] Write Protect is off
[  154.665594] sd 4:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  154.665598] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  154.674992] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  154.675003]  sdb:
[  154.684384] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  154.684393] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  178.153249] usb 1-5: USB disconnect, address 4
[  178.153382] sd 4:0:0:0: [sdb] Unhandled error code
[  178.153386] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  178.153391] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f 7b 00 00 00 08 00 00 00
[  178.153405] end_request: I/O error, dev sdb, sector 8354560
[  178.153412] __ratelimit: 12 callbacks suppressed
[  178.153417] Buffer I/O error on device sdb, logical block 8354560
[  178.153422] Buffer I/O error on device sdb, logical block 8354561
[  178.153425] Buffer I/O error on device sdb, logical block 8354562
[  178.153429] Buffer I/O error on device sdb, logical block 8354563
[  178.153433] Buffer I/O error on device sdb, logical block 8354564
[  178.153436] Buffer I/O error on device sdb, logical block 8354565
[  178.153440] Buffer I/O error on device sdb, logical block 8354566
[  178.153443] Buffer I/O error on device sdb, logical block 8354567
[  178.153678] sd 4:0:0:0: [sdb] Unhandled error code
[  178.153682] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  178.153686] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f 7b 00 00 00 08 00 00 00
[  178.153699] end_request: I/O error, dev sdb, sector 8354560
[  178.153703] Buffer I/O error on device sdb, logical block 8354560
[  178.153707] Buffer I/O error on device sdb, logical block 8354561
[  183.708044] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  183.849190] usb 1-5: configuration #1 chosen from 1 choice
[  183.851000] scsi5 : SCSI emulation for USB Mass Storage devices
[  183.866238] usb-storage: device found at 5
[  183.866243] usb-storage: waiting for device to settle before scanning
[  188.864217] usb-storage: device scan complete
[  188.865079] scsi 5:0:0:0: Direct-Access     ACTIONS  HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
[  188.867865] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  188.869181] sd 5:0:0:0: [sdb] 8354737 512-byte logical blocks: (4.27 GB/3.98 GiB)
[  188.869800] sd 5:0:0:0: [sdb] Write Protect is off
[  188.869805] sd 5:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  188.869809] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  188.877951] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  188.877962]  sdb:
[  188.888362] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  188.888371] sd 5:0:0:0: [sdb] Attached SCSI removable disk
```

But it doesn't mount, can you help me with that?

Thank you.

---

