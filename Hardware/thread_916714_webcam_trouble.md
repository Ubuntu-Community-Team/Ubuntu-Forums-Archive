---
title: "webcam trouble"
date: 2008-09-11
forum: Hardware
---

### Post by dennisgro on 2008-09-11
hi guys...been trying to install my built-in webcam, but no luck so far...tried to google it and still nothing...i`m running hardy on msi m662 laptop, and i think that i have chicony built-in camera...can someone help?? thanx in advance...

---

### Post by Casper Hansen on 2008-09-11
Try to install Cheese.

---

### Post by dennisgro on 2008-09-15
> **Casper Hansen said:**
> Try to install Cheese.

the program doesnt "see" the camera...i think i have to install drivers first... any idea how to do that??

---

### Post by IntuitiveNipple on 2008-09-15
First you need to know what the camera's PCI USB device vendor: product ID is. You can get it using:
```

lsusb

```
One of the devices listed will be the camera. You might have to guess. If you need additional clues use:
```

lsusb -v

```
but be prepared to scan through a lot of output from all USB devices to determine which is the camera. It should be obvious from mentions of 'video'.

From the vendor: product ID you can determine if any existing installed driver supports the camera by searching the kernel's list:
```

grep "vendor.*product" /lib/modules/$(uname -r)/modules.usbmap

```
The first column is the name of the driver that will handle the vendor: product ID.

---

### Post by dennisgro on 2008-09-17
> **IntuitiveNipple said:**
> First you need to know what the camera's PCI USB device vendor: product ID is. You can get it using:
```

lsusb

```
One of the devices listed will be the camera. You might have to guess. If you need additional clues use:
```

lsusb -v

```
but be prepared to scan through a lot of output from all USB devices to determine which is the camera. It should be obvious from mentions of 'video'.

From the vendor: product ID you can determine if any existing installed driver supports the camera by searching the kernel's list:
```

grep "vendor.*product" /lib/modules/$(uname -r)/modules.usbmap

```
The first column is the name of the driver that will handle the vendor: product ID.

lsusb didnt give any results (i mean, no cameras or anything that related somehow to video)...what do i do next?? i have to be able to use my camera, and i dont wanna get back to windows:lolflag:

---

