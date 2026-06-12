---
title: "Bluetooth problem in sony-vivo"
date: 2008-07-23
forum: Hardware
---

### Post by picklu on 2008-07-23
I bought a sony-vivo laptop (VGN-FZ410E). My built in bluetooth device is working fine in vista but its not working in ubuntu 8.04. But if i use any dongle then I can get connect with my mobile.

In my system bluez-utils, gnome-bluetooth, bluez-gnome are installed and its uptodate.

if i run: lsusb -v

Bus 007 Device 003: ID 044e:3010 Alps Electric Co., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x044e Alps Electric Co., Ltd
  idProduct          0x3010
  bcdDevice            0.56
  iManufacturer           1 Broadcom Corp
  iProduct                2 BCM2046 Bluetooth Device
  iSerial                 3 001E3D00B32B
  bNumConfigurations      1

can any1 help me how to use my internal bluetooth device for connecting with Nokia 6630.

---

### Post by sburns875 on 2008-09-01
Do you ever resolve this issue?  I am having the identical problem with my Vaio VGN-TZ398U with the Sony VGP-BMS33 Bluetooth Laser Mouse and Ubuntu 8.04  (all updates are current)

running "hcitool scan" does not result in any devices being found

Any ideas?

What additional information would be helpful?

---

### Post by IntuitiveNipple on 2008-09-01
Try adding the following setting:
```

echo "options hci_usb reset=1" | sudo tee -a /etc/modprobe.d/options

```
Because so many other drivers depend on **hci_usb** you can't simply unload and load it, you'll need to restart the PC to test.

The device is supported by the module, or at least is reported to be.

---

### Post by sburns875 on 2008-10-08
Just finally seeing this response...  Unfortunately this addition did not fix the problem.  Once again, I am able to browse this device, but it is unable to connect.  I *believe* that it has something to do with an inability to ftp/tftp to the device (???).  Any ideas?  What other information can I provide that would be helpful?

---

### Post by majorhabib on 2008-10-09
What is the result of running **hcitool dev**?

---

### Post by sburns875 on 2009-05-02
I found this a while ago but just upgraded to jaunty (9.04) and had to do it all over again.  Here is the link I followed:
[http://ubuntuforums.org/showthread.php?t=446422](http://ubuntuforums.org/showthread.php?t=446422)

---

