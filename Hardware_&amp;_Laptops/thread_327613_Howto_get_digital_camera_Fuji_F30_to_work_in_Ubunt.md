---
title: "Howto get digital camera Fuji F30 to work in Ubuntu"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by solitary on 2006-12-29
Hello,

I recently bought a Fuji F30 digital camera. It is not supported by default in Digikam 0.8.2  Kubuntu Edgy Eft. But it's easy to add support for it. This method seems to work for some other brands (Canon, Casio, Kodak, Nikon) and models too. :D 

Here's howto:

1 )  Connect the camera and turn it on.

2 )  Type in terminal:  ```
lsusb | grep Fuji
```
```
Bus 005 Device 005: ID 04cb:019b Fuji Photo Film Co., Ltd
```
Take note of the ID part.

3 )  Open this file in a text editor: ```
sudo nano /etc/udev/rules.d/45-libgphoto2.rules
```
```

# udev rules file for libgphoto2
#
ACTION!="add", GOTO="libgphoto2_rules_end"
SUBSYSTEM=="usb_device", GOTO="libgphoto2_rules_real"
SUBSYSTEM=="usb", GOTO="libgphoto2_rules_real"
BUS!="usb", GOTO="libgphoto2_rules_end"

LABEL="libgphoto2_rules_real"

SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06bd", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"

```

4 )  Add this line (uses values from step 2):
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="019b", MODE="0660", GROUP="plugdev"

5 ) Like this:
```
# udev rules file for libgphoto2
#
ACTION!="add", GOTO="libgphoto2_rules_end"
SUBSYSTEM=="usb_device", GOTO="libgphoto2_rules_real"
SUBSYSTEM=="usb", GOTO="libgphoto2_rules_real"
BUS!="usb", GOTO="libgphoto2_rules_end"

LABEL="libgphoto2_rules_real"
 
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="019b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06bd", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"

```

6 )  Turn off camera.

7 )  Restart udev: ```
sudo  /etc/init.d/udev restart
```

8 )  Turn on camera, start Digikam, and download you photos.


Good luck to getting your digital camera working in Ubuntu.


Notes: Original instructions are from user "dailyglen" at launchpad.net. Link to original post: [https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/64146)

---

### Post by bman77 on 2006-12-31
Your info helped me get my F20 working, thanks!

---

