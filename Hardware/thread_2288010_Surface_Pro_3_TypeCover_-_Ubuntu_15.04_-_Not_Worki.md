---
title: "Surface Pro 3 TypeCover - Ubuntu 15.04 - Not Working"
date: 2015-07-23
forum: Hardware
---

### Post by nicolae-carabut on 2015-07-23
Hi,

I have installed Ubuntu 15.04 and the TypeCover does not work even if the patch seems to be already applied for 3.19.0-23-generic.
The touchpad / mouse works not the keyboard. Where is the trick ? I have read some posts saying the opposite. 

And the whole reason for installing it was that there is no need recompile anything ...

What do I have to do ?

---

### Post by nicolae-carabut on 2015-07-23
This is the dmesg when I connect the typecover, and nothing happens

[ 3664.964108] usb 1-3: new full-speed USB device number 16 using xhci_hcd
[ 3665.092619] usb 1-3: No LPM exit latency info found, disabling LPM.
[ 3665.093664] usb 1-3: New USB device found, idVendor=045e, idProduct=07e2
[ 3665.093673] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3665.093677] usb 1-3: Product: Surface Type Cover
[ 3665.093681] usb 1-3: Manufacturer: Microsoft
[ 3665.726065] input: Microsoft Surface Type Cover UNKNOWN as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:045E:07E2.000B/input/input19
[ 3665.726518] hid-multitouch 0003:045E:07E2.000B: input,hiddev0,hidraw6: USB HID v1.11 Keyboard [Microsoft Surface Type Cover] on usb-0000:00:14.0-3/input0
[ 3665.726588] acpi PNP0C0A:00: Driver battery requests probe deferral
[ 3665.726691] acpi PNP0C0A:00: Driver battery requests probe deferral

---

### Post by tanguita on 2015-07-24
Hi, it seems you have one of new type 3 covers. Here you can see more details:

[https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/](https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/)

---

