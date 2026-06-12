---
title: "digital camera Issue"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by hamzamusa on 2008-01-13
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/22115](https://answers.launchpad.net/ubuntu/+question/22115) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi ,

I Have a strange problem , that i can not get the photos from my digital cameras , somehow , they working great on another pc ,with the same ubuntu installation with the same settings . now when i connect any of my digital cameras i get this :

"Could not get register 83. Please contact <gphoto-devel@lists.sourceforge.net>. "

somehow the same error in :

  - gThumb
  -F-Spot
  -gtkam
  -digiKam ( i can not configure it that well , or it gets the same problem as the others )

error of gtkam " An error Occurred in io-library "

all my cameras are the Olympus .

now am trying to re-install libgphoto2 . but still looking for help .

Regards

---

### Post by polmir on 2008-01-13
connect camera to pc and copy out of it:
```
lsusb
```

---

### Post by hamzamusa on 2008-01-13
> **polmir said:**
> connect camera to pc and copy out of it:
```
lsusb
```
Thanks for the first reply :

hmmm , 
by runningg lsusb

that what i get :

> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 07b4:0109 Olympus Optical Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

then same problem with : gThumb

> Could not get register 83. Please contact <gphoto-devel@lists.sourceforge.net>..

---

### Post by polmir on 2008-01-14
install or reconfigure this package:

[B]gnome-mount
gnome-volume-manager
hal
hal-cups-utils
hal-device-manager
hal-info
libhal1
libhal-storage1[/B]

for example:
```
sudo apt-get install gnome-mount
```
or
```
sudo dpkg-reconfigure gnome-mount
```

---

