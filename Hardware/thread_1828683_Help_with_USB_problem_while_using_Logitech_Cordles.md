---
title: "Help with USB problem while using Logitech Cordless Optical TrackMan"
date: 2011-08-19
forum: Hardware
---

### Post by Wydarr on 2011-08-19
Hello everybody!

I have been using Ubuntu in various flavors for the better part of the past three years, and have received a couple of months ago a Logitech Cordless Optical TrackMan. At first (a week or so), everything worked almost perfectly, but suddenly, after the upgrade to 11.04 the trackball has stopped working. 
The issue appears on various hardware configurations (Acer Aspire One, Dell Precision M6500, Asus Eee 901) and it translates in the dreaded:

> 
[  511.864220] usb 3-2: new low speed USB device using uhci_hcd and address 6
[  512.272079] usb 3-2: device not accepting address 6, error -71
[  512.272132] hub 3-0:1.0: unable to enumerate USB device on port 2


Every couple of days the trackball works for a while, until I (literally) touch the USB port in which it is plugged in, at which point "normal" service (or lack of) is resumed. The behavior is independent of the USB port that I plug the device in (it's not an issue of a defective port or cable, rather a software / configuration one, as far as I can tell).

Additionally, on one of the systems that I use I have a dual boot with a Backtrack 5 (Ubuntu 10.04 based) and I have the same issue, except I can make the trackball work every 2 or 3 reboots instead of every 10 - 20 as is the case with the 11.04. 
At the same time I have the output of a successful connection and it looks like this: 

> 
[17664.508120] usb 3-1: new low speed USB device using uhci_hcd and address 2
[17664.782851] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input11
[17664.783312] generic-usb 0003:046D:C508.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[17664.783383] usbcore: registered new interface driver usbhid
[17664.783392] usbhid: USB HID core driver


Hope any of the advanced users can help me with this issue, because I really, really love the trackball and it's a pity that I can't use it. At the same time, if there are other commands that you need output from, please let me know. 
Thanks a lot in advance.

---

