---
title: "[Trusty] Mouse Support Broken"
date: 2014-08-16
forum: Hardware
---

### Post by ndixit26 on 2014-08-16
Whenever I plug in my USB mouse in Dell Vostro 14, it goes dead after a few seconds (pointer stops moving and LED switches off). But if I click (either right or left), it starts workin after a lag of ~1 second; a few seconds later, same thing repeats.

Before plugging in:
$ lsusb
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:670b Microdia 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

After plugging in while it's working:
$ lsusb
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:670b Microdia 
Bus 001 Device 022: ID 04ca:0061 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

When it stops working:
$ lsusb
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:670b Microdia 
Bus 001 Device 022: ID 04ca:0061 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ dmesg
...
...
[ 2196.263979] usb 1-1.2: new low-speed USB device number 24 using ehci-pci
[ 2196.359973] usb 1-1.2: New USB device found, idVendor=04ca, idProduct=0061
[ 2196.359977] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2196.359979] usb 1-1.2: Product: USB Optical Mouse
[ 2196.359981] usb 1-1.2: Manufacturer: PixArt
[ 2196.362244] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input39
[ 2196.362415] hid-generic 0003:04CA:0061.001B: input,hidraw1: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[ 2197.616530] [UFW BLOCK] IN=wlan0 OUT= MAC=64:5a:04:43:8b:b3:08:bd:43:63:7e:b6:08:00 SRC=36.83.62.14 DST=10.0.0.5 LEN=58 TOS=0x00 PREC=0x00 TTL=111 ID=5446 PROTO=UDP SPT=18826 DPT=51413 LEN=38 


I know t might be a hardware flaw, but I don't have access to another machine to test it. Can anyone tell me what does above-mentioned output of dmesg suggests (I don't understand half of it)? Thanks.

---

