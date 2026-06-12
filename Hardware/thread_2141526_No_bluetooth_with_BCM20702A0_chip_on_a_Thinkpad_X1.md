---
title: "No bluetooth with BCM20702A0 chip on a Thinkpad X1 carbon"
date: 2013-05-02
forum: Hardware
---

### Post by Andrew-buntu on 2013-05-02
I recently purchased a Thinkpad X1 Carbon. Most of the hardware works OK but the Broadcom Bluetooth is not working.  Running the latest (as of this posting) packages on 13.04 - "3.8.0-19-generic" is the kernel

When turning on the computer, running lsusb doesn't show the bluetooth device and no bluetooth icon appears in my taskbar. If I open the Bluetooth GUI and flip the "On" switch, the switch stays in the "On" position but the "bluetooth is disabled" message remains. After that first switch flip, the following message appears when running dmesg:

[  221.119637] usb 1-1.4: USB disconnect, device number 16
[  221.792002] usb 1-1.4: new full-speed USB device number 17 using ehci-pci
[  221.888109] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[  221.888124] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  221.888134] usb 1-1.4: Product: BCM20702A0
[  221.888141] usb 1-1.4: Manufacturer: Broadcom Corp
[  221.888148] usb 1-1.4: SerialNumber: 9C2A70875E0B
[  221.938215] Bluetooth: can't load firmware, may not work correctly

Every time I flip the switch, the number of the device increases by one and the same series of messages appears.

Looks as if a fix may have been released last month but it's not working for me:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400)

Can someone please help me get my Bluetooth working?  I'd love to connect to my Jambox for some decent sound. I'm happy to provide any output from the Thinkpad.

---

### Post by Andrew-buntu on 2013-06-09
Think I finally fixed this by uninstalling gnome-bluetooth and reinstalling.  Still don't get an applet/indicator but that's a smaller problem.

---

