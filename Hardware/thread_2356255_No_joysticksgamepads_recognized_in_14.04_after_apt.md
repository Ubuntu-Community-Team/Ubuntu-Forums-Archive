---
title: "No joysticks/gamepads recognized in 14.04 after apt-get upgrade"
date: 2017-03-21
forum: Hardware
---

### Post by cmshowers2 on 2017-03-21
Hello!

I have a Dell XPS 8900 which has been running 14.04 for some time now and I did an apt-get upgrade on it to update all of the packages to the latest versions. It is now running kernel version 4.4.0-67-generic. I have several USB gamepads and joysticks I have been using with it which are no longer recognized as input devices (which I have confirmed by looking in /dev/input/ to see they do not appear when I plug in a device). However, they work as usual again when I boot with the old kernel I had installed (4.2.0-36-generic). I also tried installing the previous kernel release (4.4.0-66-generic) to see if it was a fluke in the 67 release but it has the same problem. Thinking that this couldn't possibly be an oversite in the released version of the kernel, I installed 4.4.0-66-generic on a nearly identical Dell XPS I have and it worked fine so this is something specific to my software/package configuration or maybe hardware (I can't check right now if my two Dell XPSes have the same motherboard but I would guess not since they are Dells).

This is my dmesg output with kernel 4.4.0-67:
[411043.062049] usb 1-8: new low-speed USB device number 14 using xhci_hcd
[411043.275426] usb 1-8: New USB device found, idVendor=046d, idProduct=c215
[411043.275435] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[411043.275440] usb 1-8: Product: Logitech Extreme 3D
[411043.275443] usb 1-8: Manufacturer: Logitech
[411043.275758] usb 1-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes

And with the 4.2.0-36 kernel I get two more lines (which I believe come out of the usb-hid driver):
[  405.567469] usb 1-8: new low-speed USB device number 7 using xhci_hcd
[  405.726858] usb 1-8: New USB device found, idVendor=046d, idProduct=c215
[  405.726864] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  405.726867] usb 1-8: Product: Logitech Extreme 3D
[  405.726869] usb 1-8: Manufacturer: Logitech
[  405.727103] usb 1-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  405.748718] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/0003:046D:C215.0004/input/input22
[  405.803486] logitech 0003:046D:C215.0004: input,hidraw2: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:14.0-8/input0


I really have no idea where to start debugging this and would appreciate any suggestions and requests for more output from the box. Thanks!

CS

---

### Post by cmshowers2 on 2017-03-21
Two things that might be relevant:
1) I have the xboxdrv package installed to support a PS3 controller I use. The PS3 controller exhibits the same behavior as the Logitech joystick in that it works fine with the old kernel and does not show up under /dev/input with the latest kernel.
2) Here is the output of usb-devices for the Logitech joystick:
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=05 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c215 Rev=02.04
S:  Manufacturer=Logitech
S:  Product=Logitech Extreme 3D
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=30mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

It is exactly the same using either kernel.

Thanks for reading!

CS

---

