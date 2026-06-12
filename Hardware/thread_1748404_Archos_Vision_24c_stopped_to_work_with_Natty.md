---
title: "Archos Vision 24c stopped to work with Natty"
date: 2011-05-03
forum: Hardware
---

### Post by Moloch85 on 2011-05-03
Hi all,

in Ubuntu 10.10 (here on my desktop PC, as usual), Kernel 2.6.35 lsusb correctly shows my mp3 player as:

Bus 001 Device 002: ID 071b:3203 Domain Technologies, Inc. Rockchip Media Player

Since I upgraded to Natty my Archos doesn't appear in the usb devices list as usual... :(
I suppose there's a Kernel bug with my device and similar ones, what should I do?

I tried the live CD too and the situation is identical.
I need advice on how to report the bug in a more precise way. At this time, I cannot mount my new mp3 player.

---

### Post by Moloch85 on 2011-05-04
This is the dmesg output when I attach the mp3 reader:

[  123.560109] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  123.753971] usbcore: registered new interface driver uas
[  123.775053] Initializing USB Mass Storage driver...
[  123.775218] usb-storage 1-1:1.0: Quirks match for vid 071b pid 3203: 80600
[  123.775257] scsi2 : usb-storage 1-1:1.0
[  123.775410] usbcore: registered new interface driver usb-storage
[  123.775413] USB Mass Storage support registered.
[  124.772911] scsi 2:0:0:0: Direct-Access              ARCHOS           1.41 PQ: 0 ANSI: 0
[  124.774478] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  124.778153] sd 2:0:0:0: [sdb] 16025600 512-byte logical blocks: (8.20 GB/7.64 GiB)
[  124.778164] sd 2:0:0:0: [sdb] Assuming Write Enabled
[  124.892144] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  125.140100] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  125.388137] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  125.636140] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  125.884143] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  126.132138] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  126.380123] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  126.572523] usb 1-1: USB disconnect, address 5
[  126.572663] sd 2:0:0:0: [sdb] No Caching mode page present
[  126.572674] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  126.575572] sd 2:0:0:0: [sdb] READ CAPACITY failed
[  126.575582] sd 2:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  126.575593] sd 2:0:0:0: [sdb] Sense not available.
[  126.575599] sd 2:0:0:0: [sdb] Assuming Write Enabled
[  126.575634] sd 2:0:0:0: [sdb] Asking for cache data failed
[  126.575642] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  126.575650] sdb: detected capacity change from 8205107200 to 0
[  126.576906] sd 2:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by karlrelton on 2011-05-13
Its a known bug.

See [https://bugzilla.kernel.org/show_bug.cgi?id=35042](https://bugzilla.kernel.org/show_bug.cgi?id=35042)

---

### Post by karlrelton on 2011-05-22
It is now fixed in the upstream 2.6.38.7 stable release, so should find its way into a stock Natty kernel update in the not too distant future.

---

