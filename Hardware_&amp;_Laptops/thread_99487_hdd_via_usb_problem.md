---
title: "hdd via usb problem"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by clarknova on 2005-12-05
Hi,

I have a usb-ide adaptor that appeared to work well on my brother's WinXP machine, but I can't get it to connect. Here are some ouput-like things that you may find informative. Thanks.

db

[FONT="Fixedsys"]$ dmesg | grep usb
[4325536.366000] usb 3-3: new high speed USB device using ehci_hcd and address 24
[4325536.446000] usb-storage: device found at 24
[4325536.446000] usb-storage: waiting for device to settle before scanning
[4325536.699000] usb 3-3: USB disconnect, address 24
[4325536.870000] usb 3-3: new high speed USB device using ehci_hcd and address 25
[4325537.334000] usb 3-3: device not accepting address 25, error -71

$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04f9:0162 Brother Industries, Ltd
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

$ lsmod | grep usb
usblp                  12640  0
usb_storage            74112  0
scsi_mod              135688  4 sr_mod,sbp2,sd_mod,usb_storage
usbhid                 35264  0
usbcore               118044  6 usblp,usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_core              138772  5 usb_storage,ide_cd,ide_disk,ide_generic,sis5513[/FONT]

---

