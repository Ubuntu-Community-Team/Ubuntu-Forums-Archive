---
title: "MP3-player not mounted/recognized"
date: 2010-12-26
forum: Hardware
---

### Post by Taiyou on 2010-12-26
Hello,

I recently received an mp3-player as a gift. But ubuntu (10.10) doesn't seem to be able to recognize it.

I have tried 'lsusb', but it wasn't listed.
When I do 'sudo fdisk -l' it's also not listed as for example '/dev/sdb' or something.

This is the output of 'dmesg'
```
[19571.732541] usb 1-4: new high speed USB device using ehci_hcd and address 2
[19571.889154] scsi7 : usb-storage 1-4:1.0
[19572.883155] scsi 7:0:0:0: Direct-Access     TS300    USB DISK         1.00 PQ: 0 ANSI: 0
[19572.885856] sd 7:0:0:0: Attached scsi generic sg2 type 0
[19572.887266] sd 7:0:0:0: [sdb] 7868416 512-byte logical blocks: (4.02 GB/3.75 GiB)
[19573.012547] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19573.292550] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19573.572565] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19573.725019] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[19573.725024] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19573.728521] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[19575.333015] sd 7:0:0:0: [sdb] 7868416 512-byte logical blocks: (4.02 GB/3.75 GiB)
[19575.452547] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19580.603253] usb 1-4: device descriptor read/all, error -110
[19580.722560] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19595.842579] usb 1-4: device descriptor read/64, error -110
[19611.072656] usb 1-4: device descriptor read/64, error -110
[19611.302540] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19616.332568] usb 1-4: device descriptor read/8, error -110
[19621.462692] usb 1-4: device descriptor read/8, error -110
[19621.692551] usb 1-4: reset high speed USB device using ehci_hcd and address 2
[19626.722567] usb 1-4: device descriptor read/8, error -110
[19631.852802] usb 1-4: device descriptor read/8, error -110
[19631.962587] usb 1-4: USB disconnect, address 2
[19631.962587] sd 7:0:0:0: Device offlined - not ready after error recovery
[19631.962840] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19631.965104] sd 7:0:0:0: [sdb] READ CAPACITY failed
[19631.965109] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[19631.965112] sd 7:0:0:0: [sdb] Sense not available.
[19631.965125] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19631.965130] sdb: detected capacity change from 4028628992 to 0
[19632.130042] usb 1-4: new high speed USB device using ehci_hcd and address 3
[19647.242550] usb 1-4: device descriptor read/64, error -110
[19662.472560] usb 1-4: device descriptor read/64, error -110
[19662.702566] usb 1-4: new high speed USB device using ehci_hcd and address 4
[19677.822587] usb 1-4: device descriptor read/64, error -110
[19693.052575] usb 1-4: device descriptor read/64, error -110
[19693.282582] usb 1-4: new high speed USB device using ehci_hcd and address 5
[19698.312600] usb 1-4: device descriptor read/8, error -110
[19703.442594] usb 1-4: device descriptor read/8, error -110
[19703.672548] usb 1-4: new high speed USB device using ehci_hcd and address 6
[19708.702581] usb 1-4: device descriptor read/8, error -110
[19713.840077] usb 1-4: device descriptor read/8, error -110
[19713.942555] hub 1-0:1.0: unable to enumerate USB device on port 4
[19714.262545] usb 4-2: new full speed USB device using uhci_hcd and address 2
[19729.382549] usb 4-2: device descriptor read/64, error -110
[19744.612534] usb 4-2: device descriptor read/64, error -110
[19744.842543] usb 4-2: new full speed USB device using uhci_hcd and address 3
[19759.962714] usb 4-2: device descriptor read/64, error -110
[19775.200047] usb 4-2: device descriptor read/64, error -110
[19775.422630] usb 4-2: new full speed USB device using uhci_hcd and address 4
[19780.444498] usb 4-2: device descriptor read/8, error -110
[19785.574491] usb 4-2: device descriptor read/8, error -110
[19785.802547] usb 4-2: new full speed USB device using uhci_hcd and address 5
[19790.824490] usb 4-2: device descriptor read/8, error -110
[19795.961473] usb 4-2: device descriptor read/8, error -110
[19796.062556] hub 4-0:1.0: unable to enumerate USB device on port 2

```

any suggestions are welcome!

---

