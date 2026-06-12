---
title: "Keyboard and nouse detectect but not working"
date: 2019-07-22
forum: Hardware
---

### Post by a_gautier on 2019-07-22
Hi there
I have a KVM working perfectly under Windows but under Ubuntu 19.1 (and Linux in general) the keyboard and mouse are not working, whatever the PC or laptop used. It is working in the grub menu. "lsusb -v" shows that the Chinese manufacturer of the KVM switch did something pretty stupid, it used Logitech idVendor (0x046d) and Unifying Receiver idProduct (0xc52b) for their KVM, and did it badly enough to forget iManufacturer and iProduct value (reported=0). With no iManufacturer and no iProduct Linux detects the USB peripheral but stop loading any driver (as show in syslog and dmesg). How can I force-load the generic HID-compliant driver under Ubuntu for this USB KVM switch? I attached an extract [FONT=&amp]lsusb -v [/FONT]and past below a piece of dmesg. Connected to usb 4 is the KVM, on usb 5 is a Logitech Unifying receiver as a matter of comparison. 
Thanks

dmesg
First, plugging the KVM switch USB connector
```
[ 5257.711222] usb 4-1: new low-speed USB device number 4 using ohci-pci
[ 5257.902842] usb 4-1: New USB device found, idVendor=046d, idProduct=c52b
[ 5257.902850] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```
it stops here, nothing else with the KVM switch detection
Second, plugging a genuine Unifying Receiver:
```

[ 5315.018159] usb 5-2: new full-speed USB device number 3 using ohci-pci
[ 5315.218855] usb 5-2: New USB device found, idVendor=046d, idProduct=c52b
[ 5315.218863] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5315.218867] usb 5-2: Product: USB Receiver
[ 5315.218871] usb 5-2: Manufacturer: Logitech
[ 5315.239303] logitech-djreceiver 0003:046D:C52B.000D: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-2/input2
[ 5315.388332] input: Logitech MX Anywhere 2S as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.2/0003:046D:C52B.000D/0003:046D:406A.000E/input/input14
[ 5315.389598] logitech-hidpp-device 0003:046D:406A.000E: input,hidraw1: USB HID v1.11 Keyboard [Logitech MX Anywhere 2S] on usb-0000:00:13.0-2:1
```

---

