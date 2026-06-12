---
title: "External hardrive fails to mount."
date: 2018-07-31
forum: Hardware
---

### Post by eugenio.myles on 2018-07-31
Hello, I'm troubleshooting an external hardrive for photographer friend. She has a year's worth of photos stored on the external drive, unfortunately, Windows (her go-to operating system) does not recognize nor mount it. It would be nice to recover the information, even if the hardrive is trashed.

The hardrive is a BUP Slim SL disk-drive with a usb connector, manufactured by Seagate. I've plugged it into a working usb drive (pre-tested with another device for assurance) on a machine running Ubuntu. I have attempted the following:

(1): Tried fdisk, which _never_ recognizes the drive.
```

sudo fdisk -l

```

(2): I tried twice successively.
```

dmesg | tail -n 20

```

At first, the drive is recognized:
```

[user]$ dmesg | tail -n 20
[75790.056781] usb 2-1.5: new high-speed USB device number 8 using ehci-pci
[75790.223408] usb 2-1.5: New USB device found, idVendor=0bc2, idProduct=ab26
[75790.223415] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[75790.223420] usb 2-1.5: Product: BUP Slim SL
[75790.223424] usb 2-1.5: Manufacturer: Seagate
[75790.223429] usb 2-1.5: SerialNumber: NA9DCBRL
[75790.225879] scsi host11: uas
[75790.226838] scsi 11:0:0:0: Direct-Access     Seagate  BUP Slim SL      0108 PQ: 0 ANSI: 6
[75790.246556] sd 11:0:0:0: Attached scsi generic sg7 type 0

```
In this brief window of time before disk spin-up, sg7 appears in /dev:
```

[user]$ ls /dev | grep sg
bsg
kmsg
sg0
sg1
sg2
sg3
sg4
sg5
sg6
sg7

```

A few moments later, I check dmesg again to find the disk spinning up and the following output:
```

[user]$ dmesg | tail -n 20
[75790.246556] sd 11:0:0:0: Attached scsi generic sg7 type 0
[75798.642812] sd 11:0:0:0: [sdf] Spinning up disk...
[75800.421000] usb 2-1.5: stat urb: status -71
[75800.632234] usb 2-1.5: USB disconnect, device number 8
[75800.632402] sd 11:0:0:0: tag#0 uas_zap_pending 0 uas-tag 1 inflight: CMD 
[75800.632410] sd 11:0:0:0: tag#0 CDB: Test Unit Ready 00 00 00 00 00 00
[75800.366209] .ready
[75800.722111] sd 11:0:0:0: [sdf] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[75800.722120] sd 11:0:0:0: [sdf] Sense not available.
[75800.812119] sd 11:0:0:0: [sdf] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[75800.812127] sd 11:0:0:0: [sdf] Sense not available.
[75800.878119] sd 11:0:0:0: [sdf] Write Protect is off
[75800.878128] sd 11:0:0:0: [sdf] Mode Sense: 00 00 00 00
[75800.908167] sd 11:0:0:0: [sdf] Asking for cache data failed
[75800.908176] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[75801.084129] sd 11:0:0:0: [sdf] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[75801.084137] sd 11:0:0:0: [sdf] Sense not available.
[75801.174187] sd 11:0:0:0: [sdf] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[75801.174194] sd 11:0:0:0: [sdf] Sense not available.
[75801.324120] sd 11:0:0:0: [sdf] Attached SCSI disk

```
There appears to be some error upon spin-up, however I am unable to garner much else from this output. I tried searching the inter-webs for 'dmesg: status -71' with no luck. Also, at this point, the device dissapears from /dev:
```

[user]$ ls /dev | grep sg
bsg
kmsg
sg0
sg1
sg2
sg3
sg4
sg5
sg6

```

Is the drive salvagable? Are the _stored photos_ salvagable, independent of the drive? Any help would be greatly appreciated!

May the Force be with you,
Paul
.

---

