---
title: "scsi emulation not kicking in while connecting lacie lacinema black"
date: 2009-06-29
forum: Hardware
---

### Post by orentini on 2009-06-29
hi,

just bought a Lacie Lacinema black max, 1 TB.
it's basically a USB external hdd, streamer, and tv tuner.

when connecting it to my ubuntu 8.10 PC (or 9.04 laptop) via USB no auto-mounting happens.

this is what I get:
```

lsusb

Bus 001 Device 004: ID 059f:1025 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

dmesg |grep usb
[ 4558.529036] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 4558.661666] usb 1-5: configuration #3 chosen from 1 choice

```

```
dmesg |grep scsi 
``` is empty.

no /dev/sd* is created.

and last but not least:
```

lsmod|grep usb

usb_storage            83136  0 
libusual               29844  1 usb_storage
usbhid                 35712  0 
hid                    50560  1 usbhid
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
usbcore               149488  6 ehci_hcd,usb_storage,libusual,usbhid,uhci_hcd

```


please help, why isn't it working for me?

thanks,
Oren.

---

### Post by orentini on 2009-06-30
just thought i'd mention that scsi emulator is kicking in for usb mp3 player for example..
Lacie tech support says that the lacinema should work the same way too..

any ideas? please?

---

### Post by orentini on 2009-07-08
bump

---

### Post by orentini on 2009-07-15
someone?

---

### Post by orentini on 2009-07-26
anyone?

---

### Post by orentini on 2009-09-26
a workaround -
worked for me after updating the firmware of the machine, and using latest Windows VirtualBox.

---

