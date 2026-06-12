---
title: "Logitech M545 Protocol spec without prior Class and Subclass spec at line 17398"
date: 2015-01-11
forum: Hardware
---

### Post by Geriro on 2015-01-11
Hello,

Bought a Logitech M545 (wireless mouse) for my laptop yesterday. Connected it and it was working fine.
Today when i woke up the laptop from suspend, the wireless mouse did not work.

Did a lsusb and got this:

Protocol spec without prior Class and Subclass spec at line 17398  <--- hm...
Bus 001 Device 006: ID 24ae:2001      <----------------------------------------- mouse
Bus 001 Device 003: ID 04f2:b3d5 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

(it removes when i unplug the usb receiver/dongle)


Relevant info from dmesg
----------------------------------
(...)
[ 1114.959810] usb 1-1: new full-speed USB device number 6 using xhci_hcd
[ 1114.978344] usb 1-1: New USB device found, idVendor=24ae, idProduct=2001
[ 1114.978349] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1114.978351] usb 1-1: Product: RAPOO 5G Wireless Device
[ 1114.978353] usb 1-1: Manufacturer: RAPOO
[ 1114.978485] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1114.978491] usb 1-1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 1114.979957] input: RAPOO RAPOO 5G Wireless Device as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input25
[ 1114.980060] hid-generic 0003:24AE:2001.0005: input,hidraw0: USB HID v1.01 Keyboard [RAPOO RAPOO 5G Wireless Device] on usb-0000:00:14.0-1/input0
[ 1114.982791] input: RAPOO RAPOO 5G Wireless Device as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/input/input26
[ 1114.983162] hid-generic 0003:24AE:2001.0006: input,hiddev0,hidraw1: USB HID v1.01 Mouse [RAPOO RAPOO 5G Wireless Device] on usb-0000:00:14.0-1/input1


I've looked in the usb.ids list for "RAPOO", but i didn't find anything. Logitech shows up tho.. :


  % cat /usr/share/hwdata/usb.ids | grep Logitech                                                                                                                                         !602
	2c24  Logitech M-UAL-96 Mouse
	c359  Logitech Harmony
046d  Logitech, Inc.
	040f  Logitech/Storm PageScan
	0a03  Logitech USB Microphone
	c218  Logitech RumblePad 2 USB
	c529  Logitech Keyboard + Mice
	0201  USB Keyboard [Alps or Logitech, M2452]
	0607  Logitech G110 Hub




I did a sudo update-usbids, but no luck.

I guess i have to add RAPOO to the usb.ids, but i dont know what to add.

From my understanding, RAPOO is the manufacturer/producer of this mouse, but it's sold under Logitech. Correct me if im wrong.

Please help. I don't know what to do!

---

### Post by Geriro on 2015-01-11
It was my sister pulling the lamest joke ever by switching usb receivers... omg.

---

