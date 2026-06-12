---
title: "Udev / Permissions / Digital Camera"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by limewolf on 2005-05-21
My digital camera is causing some problems (a Canon PowerShot A60)....

It seems to work ok as root using gphoto2 but when I try and use it via a normal user it gives me an error. I suspect this is just a permission problem (to do with udev?)  -  what can i do to try and fix this?

The error is get as a normal user is:

> [chris@arcticwolf ~]$ gphoto2 -P

*** Error ***
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
*** Error (-53: 'Could not claim the USB device') ***

I've no idea how i can find out what device the camera is using (to change permissions in the udev config (/etc/udev/udev.permissions
 ?)

Any help would be appreciated (I'll supply any extra info as required), Thanks!

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=limewolf]My digital camera is causing some problems (a Canon PowerShot A60)....

It seems to work ok as root using gphoto2 but when I try and use it via a normal user it gives me an error. I suspect this is just a permission problem (to do with udev?)  -  what can i do to try and fix this?

The error is get as a normal user is:



I've no idea how i can find out what device the camera is using (to change permissions in the udev config (/etc/udev/udev.permissions
 ?)

Any help would be appreciated (I'll supply any extra info as required), Thanks![/QUOTE]

I have the same problem. I never found the fix, but I have learned to start my camera program (I like digikam) with a gksudo. Like:

gksudo gphoto2


I like it now because it allows me to view the pics without accedental deletion.

---

### Post by limewolf on 2005-05-22
It seems a bit drastic to run a program as root, to work around a problem that should be fixable (at least in theory :-)).

Is there a way i can identify the device (in /dev/) that the camera is using?

Thanks.

---

### Post by David Haas on 2005-05-22
This article in Tuxme.com at <http://www.tuxme.com/node/436> alerted me to download images from my Nikon Coolpix 3700 to Ubuntu Hoary using gThumb image viewer (Applications>Graphics>gThumb image viewer). It works great. I connect the camera to a USB port, turn it on, and open gThumb. Instantly all the stored images are seen as thumbnails in gThumb-even without clicking the download button on the camera. At first, gThumb asked me to select my camera from its stored list. Might this method work for you?
David

---

