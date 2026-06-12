---
title: "usb hdd makes awful noises"
date: 2008-09-09
forum: Hardware
---

### Post by excogitation on 2008-09-09
The harddrive is encrypted (whole disk) using Truecrypt.
It's in a SATA/USB <-> PATA & SATA housing and I connect it with USB to my laptop.

```
# lsusb
Bus 005 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
```

```
# fdisk -l
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2e3c1f6

Disk /dev/sdb doesn't contain a valid partition table

```
After a while just makes those awful clicking noises.
Using it in Windows works just fine (no unexpected noise).

```
# dmesg
[55072.064065] usb 5-4: new high speed USB device using ehci_hcd and address 4
[55072.228846] usb 5-4: configuration #1 chosen from 1 choice
[55072.267819] scsi3 : SCSI emulation for USB Mass Storage devices
[55072.274405] usb-storage: device found at 4
[55072.274416] usb-storage: waiting for device to settle before scanning
[55077.272472] usb-storage: device scan complete
[55077.275329] scsi 3:0:0:0: Direct-Access     ST980815 A                D    PQ: 0 ANSI: 2 CCS
[55077.319487] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[55077.323042] sd 3:0:0:0: [sdb] Write Protect is off
[55077.323057] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[55077.323063] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[55077.331449] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[55077.334181] sd 3:0:0:0: [sdb] Write Protect is off
[55077.334195] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[55077.334201] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[55077.335179]  sdb:<6>sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.000496] end_request: I/O error, dev sdb, sector 0
[55089.000510] Buffer I/O error on device sdb, logical block 0
[55089.002304] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.002319] end_request: I/O error, dev sdb, sector 0
[55089.002326] Buffer I/O error on device sdb, logical block 0
[55089.005228] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.005242] end_request: I/O error, dev sdb, sector 0
[55089.005249] Buffer I/O error on device sdb, logical block 0
[55089.012360] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.012379] end_request: I/O error, dev sdb, sector 0
[55089.012388] Buffer I/O error on device sdb, logical block 0
[55089.017457] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.017468] end_request: I/O error, dev sdb, sector 0
[55089.017475] Buffer I/O error on device sdb, logical block 0
[55089.017501] ldm_validate_partition_table(): Disk read failed.
[55089.017753] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.017762] end_request: I/O error, dev sdb, sector 0
[55089.017769] Buffer I/O error on device sdb, logical block 0
[55089.018120] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.018135] end_request: I/O error, dev sdb, sector 0
[55089.018143] Buffer I/O error on device sdb, logical block 0
[55089.018416] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.018426] end_request: I/O error, dev sdb, sector 0
[55089.018433] Buffer I/O error on device sdb, logical block 0
[55089.019117] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.019127] end_request: I/O error, dev sdb, sector 0
[55089.019134] Buffer I/O error on device sdb, logical block 0
[55089.019158] Dev sdb: unable to read RDB block 0
[55089.019330] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.019340] end_request: I/O error, dev sdb, sector 0
[55089.019599] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.019609] end_request: I/O error, dev sdb, sector 0
[55089.020248] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.020259] end_request: I/O error, dev sdb, sector 24
[55089.021051] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.021061] end_request: I/O error, dev sdb, sector 24
[55089.021259] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.021269] end_request: I/O error, dev sdb, sector 0
[55089.021462] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[55089.021471] end_request: I/O error, dev sdb, sector 0
[55089.021493]  unable to read partition table
[55089.026369] sd 3:0:0:0: [sdb] Attached SCSI disk
[55089.026598] sd 3:0:0:0: Attached scsi generic sg2 type 0
[55089.073268] usb 5-4: USB disconnect, address 4
[55101.344414] ACPI: \_SB_.PCI0.SATA.SECD.BAY_: found ejectable bay
[55101.344427] ACPI: \_SB_.PCI0.SATA.SECD.BAY_: Adding notify handler
[55101.346551] ACPI: Error installing bay notify handler
[55126.784051] usb 5-4: new high speed USB device using ehci_hcd and address 5
[55126.971125] usb 5-4: configuration #1 chosen from 1 choice
[55126.999189] scsi4 : SCSI emulation for USB Mass Storage devices
[55127.003346] usb-storage: device found at 5
[55127.003358] usb-storage: waiting for device to settle before scanning
[55132.000389] usb-storage: device scan complete
[55132.001998] scsi 4:0:0:0: Direct-Access     ST980815 A                D    PQ: 0 ANSI: 2 CCS
[55132.054898] sd 4:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[55132.057217] sd 4:0:0:0: [sdb] Write Protect is off
[55132.057230] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[55132.057251] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[55132.060750] sd 4:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[55132.062765] sd 4:0:0:0: [sdb] Write Protect is off
[55132.062777] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[55132.062783] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[55132.067669]  sdb: unknown partition table
[55132.087338] sd 4:0:0:0: [sdb] Attached SCSI disk
[55132.088320] sd 4:0:0:0: Attached scsi generic sg2 type 0
[55155.204177] usb 5-4: USB disconnect, address 5

```

---

### Post by excogitation on 2008-09-18
*bump*

---

### Post by IntuitiveNipple on 2008-09-18
Is the external device self-powered or drawing its power from the PC's USB bus? It is worth using an external power source to test whether or not this is the problem.
It can also help to connect the device directly to the PC if it is connected via a USB hub.

Very often these types of errors are caused by weird power issues. I've seen it several times and often they are hard to explain convincingly especially when Windows doesn't exhibit the same issue.

Take a look in the Ubuntu Launchpad bug-tracker. There are [several bugs reported of similar nature](https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=hostbyte%3DDID_ERROR&orderby=-importance&search=Search).

---

