---
title: "external LG HL-DT-ST DVDRAM GSA-5163D since Feisty malfunctioned"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by _obelix_ on 2007-05-20
Hi,

my external LG HL-DT-ST DVDRAM GSA-5163D A104 since Feisty malfunctioned. I connected the Writer over USB and the dmesg output is:

```
[10948.069787] usb 4-2: device descriptor read/64, error -71
[10948.285442] usb 4-2: device descriptor read/64, error -71
[10948.501113] usb 4-2: reset high speed USB device using ehci_hcd and address 39
[10948.904498] usb 4-2: device not accepting address 39, error -71
[10949.016341] usb 4-2: reset high speed USB device using ehci_hcd and address 39
[10949.423712] usb 4-2: device not accepting address 39, error -71
[10949.423761] usb 4-2: USB disconnect, address 39
[10949.535552] usb 4-2: new high speed USB device using ehci_hcd and address 40
[10949.647383] usb 4-2: device descriptor read/64, error -71
[10949.863053] usb 4-2: device descriptor read/64, error -71
[10950.078728] usb 4-2: new high speed USB device using ehci_hcd and address 41
[10950.190556] usb 4-2: device descriptor read/64, error -71
[10950.406230] usb 4-2: device descriptor read/64, error -71
[10950.621900] usb 4-2: new high speed USB device using ehci_hcd and address 42
[10951.025276] usb 4-2: device not accepting address 42, error -71
[10951.137117] usb 4-2: new high speed USB device using ehci_hcd and address 43
[10951.540491] usb 4-2: device not accepting address 43, error -71
[10972.005422] usb 4-2: new high speed USB device using ehci_hcd and address 44
[10972.275059] usb 4-2: configuration #1 chosen from 1 choice
[10972.390737] scsi8 : SCSI emulation for USB Mass Storage devices
[10972.393592] usb-storage: device found at 44
[10972.393600] usb-storage: waiting for device to settle before scanning
[10977.377411] usb-storage: device scan complete
[10977.489130] usb 4-2: reset high speed USB device using ehci_hcd and address 44
[10977.596971] usb 4-2: device descriptor read/64, error -71
[10977.812635] usb 4-2: device descriptor read/64, error -71
[10978.028319] usb 4-2: reset high speed USB device using ehci_hcd and address 44
[10978.140138] usb 4-2: device descriptor read/64, error -71
[10978.355808] usb 4-2: device descriptor read/64, error -71
[10978.571480] usb 4-2: reset high speed USB device using ehci_hcd and address 44
[10978.978855] usb 4-2: device not accepting address 44, error -71
[10979.090692] usb 4-2: reset high speed USB device using ehci_hcd and address 44
[10979.498067] usb 4-2: device not accepting address 44, error -71
[10979.498113] usb 4-2: USB disconnect, address 44
[10979.617897] usb 4-2: new high speed USB device using ehci_hcd and address 45
[10979.729728] usb 4-2: device descriptor read/64, error -71
[10979.945400] usb 4-2: device descriptor read/64, error -71
[10980.161080] usb 4-2: new high speed USB device using ehci_hcd and address 46
[10980.272905] usb 4-2: device descriptor read/64, error -71
[10980.488572] usb 4-2: device descriptor read/64, error -71
[10980.704259] usb 4-2: new high speed USB device using ehci_hcd and address 47
[10981.111632] usb 4-2: device not accepting address 47, error -71
[10981.223480] usb 4-2: new high speed USB device using ehci_hcd and address 48
[10981.630852] usb 4-2: device not accepting address 48, error -71
[11001.960046] usb 4-2: new high speed USB device using ehci_hcd and address 49
[11002.229495] usb 4-2: configuration #1 chosen from 1 choice
[11002.229760] scsi9 : SCSI emulation for USB Mass Storage devices
[11002.229903] usb-storage: device found at 49
[11002.229905] usb-storage: waiting for device to settle before scanning
[11007.212192] usb-storage: device scan complete
[11007.331908] usb 4-2: reset high speed USB device using ehci_hcd and address 49
```

When I use Firewire to connect the Writer and burn Data, then:

```
May 18 19:47:29 obelix kernel: [18947.484704] ieee1394: sbp2: aborting sbp2 command
May 18 19:47:29 obelix kernel: [18947.484713] sr 12:0:0:0:
May 18 19:47:29 obelix kernel: [18947.484715]         command: Read Capacity(10): 25 00 00 00 00 00 00 00 00 00
May 18 19:48:04 obelix kernel: [18981.750176] ieee1394: sbp2: aborting sbp2 command
May 18 19:48:04 obelix kernel: [18981.750186] sr 12:0:0:0:
May 18 19:48:04 obelix kernel: [18981.750188]         command: Read Capacity(10): 25 00 00 00 00 00 00 00 00 00
usw.
usw.
```

I install Packet Writing to use DVD-RAM. Just when copy Data to the DVD-RAM, then starts the copy Job for a moment. After a moment in /var/log/messages / dmesg:

```
[18275.415886] attempt to access beyond end of device
[18275.415895] sr0: rw=0, want=3493116, limit=2097151
[18275.416027] udf: udf_read_inode(ino 873278) failed !bh
[18275.416067] attempt to access beyond end of device
[18275.416071] sr0: rw=0, want=3642976, limit=2097151
[18275.416073] udf: udf_read_inode(ino 910743) failed !bh
[18278.879465] attempt to access beyond end of device
[18278.879477] sr0: rw=0, want=3493116, limit=2097151
[18278.879483] udf: udf_read_inode(ino 873278) failed !bh
[18278.975515] attempt to access beyond end of device
[18278.975526] sr0: rw=0, want=3493116, limit=2097151
[18278.975531] udf: udf_read_inode(ino 873278) failed !bh
[18282.641556] attempt to access beyond end of device
[18282.641567] sr0: rw=0, want=3642976, limit=2097151
[18282.641573] udf: udf_read_inode(ino 910743) failed !bh
[18282.642288] attempt to access beyond end of device
[18282.642292] sr0: rw=0, want=3642976, limit=2097151
[18282.642295] udf: udf_read_inode(ino 910743) failed !bh
```

Thanks for Help.

Best regards.

Obelix

EDIT: I hope my english is OK

---

### Post by _obelix_ on 2007-05-25
Hi,

i tested the writer with Knoppix 5.2. USB & Firewire works fine. I look at launchpad but nothing found. 

Have anybody a idea?


Thanks.

Obelix

---

