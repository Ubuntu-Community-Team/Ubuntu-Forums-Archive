---
title: "How do i install a Magstripe card reader in Ububtu 9.04"
date: 2009-05-07
forum: Hardware
---

### Post by unavenged on 2009-05-07
Hi, I need to install a USB magstripe card reader for a POS machine but it doesn't work... Can some one please help me to set it up?

The only info i have is the model number printed at the bottom: MMSR-33-UB
and when i use #lsusb i get this: Bus 006 Device 002: ID 1130:0001 Tenx Technology, Inc.

Thanks

---

### Post by unavenged on 2009-05-12
I just testes the card reader under Ubuntu 8.10 and it works fine... when we ran #dmesg in Ubuntu 8.10 terminal we got the following
[ 9780.065043] usb 1-1: new low speed USB device using ohci_hcd and address 5
[ 9780.231304] usb 1-1: configuration #1 chosen from 1 choice
[ 9780.244928] input: USB-TMU-V1 as /devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1:1.0/input/input13
[ 9780.294188] input,hidraw3: USB HID v1.10 Keyboard [USB-TMU-V1] on usb-0000:00:12.0-1

But when I ran it in Ubuntu 9.04 terminal I got the following

[ 9775.137210] usb 6-2: new low speed USB device using uhci_hcd and address 2
[ 9775.303807] usb 6-2: configuration #1 chosen from 1 choice

It seems like it doesn't detect it as a input device under Ubuntu 9.04

---

### Post by unavenged on 2009-05-12
I got it work

just do the following in terminal

#sudo gedit /etc/modules

and under the "lp" line add "usbkbd"

It should load it if it is plugged in at startup

---

