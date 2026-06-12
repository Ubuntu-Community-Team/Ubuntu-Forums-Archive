---
title: "How to &quot;register usb thing&quot; as device?"
date: 2016-03-07
forum: Hardware
---

### Post by ThomasDenmark on 2016-03-07
I have a Teensy (Arduino analog). When I plug in the usb cable, it pops up in /dev, as /dev/ttyACM0. The Teensy has a reset button. If I press it, it disappears from /dev, and does not come back. 

Below is the print out from dmesg. I have added line breaks and comments. 

```
# removing usb cable
[  854.127430] usb 3-3: USB disconnect, device number 14

# inserting usb cable
[  856.454967] usb 3-3: new full-speed USB device number 15 using xhci_hcd
[  856.584344] usb 3-3: New USB device found, idVendor=16c0, idProduct=0483
[  856.584359] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  856.584365] usb 3-3: Product: USB Serial
[  856.584371] usb 3-3: Manufacturer: Teensyduino
[  856.584376] usb 3-3: SerialNumber: 1291970
[  856.585285] cdc_acm 3-3:1.0: This device cannot do calls on its own. It is not a modem.
[  856.585328] cdc_acm 3-3:1.0: ttyACM0: USB ACM device

# pressing reset button
[  859.819481] usb 3-3: USB disconnect, device number 15
[  860.277756] usb 3-3: new full-speed USB device number 16 using xhci_hcd
[  860.406277] usb 3-3: New USB device found, idVendor=16c0, idProduct=0478
[  860.406289] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[  860.406294] usb 3-3: SerialNumber: 0001F8AD
[  860.407754] hid-generic 0003:16C0:0478.000B: hidraw5: USB HID v1.11 Device [HID 16c0:0478] on usb-0000:00:14.0-3/input0

```

I need to "register" it in /dev. I don't know the proper terms nor the logic/structure behind this. But I need to work with it as  /dev/ttyACM0 (or different naming), without having to manually plug the usb cable in and out. 

Is there some solution to this?

Sincerely

---

### Post by sudodus on 2016-03-07
I don't know the Teensy, but a USB pendrive can behave in a similar way to what you describe. If you 'eject' it, you have to unplug and plug it back again. I think 'eject' will turn it off, some electronic switch is turned off. If you 'unmount' it with the linux command ***umount***, it will still be recognized as a mass storage device (for example /dev/sdb) and it can be mounted with the linux command ***mount***.

Maybe your Teensy behaves in a similar way also with the mount and umount commands. Is it necessary to 'reset' it with its button, or would it work to unmount it?

In that case you can make a mountpoint (only once)

```
sudo mkdir /mnt/teensy
```

and try with the following commands

```
sudo umount /dev/ttyACM0
...
...
sudo mount /dev/ttyACM0 /mnt/teensy
```

Maybe the device cannot be mounted like this at all.

It is also possible that you have to keep unplugging and plugging it back after reset.

---

### Post by ThomasDenmark on 2016-03-07
Thanks. A Teensy is not a storage device. At least not in my understanding. I dont think "mounting" is a relevant word here. I could be wrong.... and unfortunately it is not an option to manually unplug plug.

---

### Post by sudodus on 2016-03-07
It means that you need some special driver. Maybe you can find ***linux drivers*** at the web site of the manufacturers of Teensy.

---

