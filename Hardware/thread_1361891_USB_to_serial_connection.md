---
title: "USB to serial connection"
date: 2009-12-22
forum: Hardware
---

### Post by WkenCouser on 2009-12-22
Hello,

I am trying under Wine to use my Golflogix GPS device. I am using the latest version Karmic Koala.

I have installed the PL2303 drivers but the when I turn on the device it is not seen by the computer. 
I am new to Ubuntu so I would appreciate some assistance.  Please be gentle with me as I am willing to learn but do not know where to start.
Thank you in advance for your kind assistance.

Once I am able to use Golflogix and my TomTom with Ubuntu I will no longer need Windows.

W. Ken Couser


Details of different commands are 
wken@mwcc:~$ uname -r
2.6.31-16-generic

wken@mwcc:~$ dmesg
[17808.868128] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17809.029357] usb 2-1: configuration #1 chosen from 1 choice
[17809.051018] usbcore: registered new interface driver usbserial
[17809.051048] USB Serial support registered for generic
[17809.051100] usbcore: registered new interface driver usbserial_generic
[17809.051104] usbserial: USB Serial Driver core
[17809.057627] USB Serial support registered for pl2303
[17809.057652] pl2303 2-1:1.0: pl2303 conv

wken@mwcc:~$ sudo lsusb -v -d 067b:2303
bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
erter detected
[17809.069294] usb 2-1: pl2303 converter now attached to ttyUSB0
[17809.069325] usbcore: registered new interface driver pl2303
[17809.069330] pl2303: Prolific PL2303 USB to serial adaptor driver
[17809.147149] pl2303 ttyUSB0: pl2303_open - failed submitting read urb, error -22

---

### Post by WkenCouser on 2010-06-06
Hello,

I have now done a clean install of Lucid Lynx.

Any ideas anyone?

Thanks,
Ken :-)

---

### Post by Austin25 on 2010-06-06
Are you using Linux drivers or Windows drivers under wine?

---

