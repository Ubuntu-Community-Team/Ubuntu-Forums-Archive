---
title: "Kodak C300 digital camera only accessed as root"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by librano on 2007-06-15
hi everyone!

I am trying to get my Kodak C300 digital camera working with Ubuntu Edgy. I am able to import photos and movies from the camera when I run digikam with root privileges... everything works fine... however, as a normal user, Ubuntu detects the camera, pops up a dialogue to import the pictures but then comes up with this error

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim
 interface 0 (Operation not permitted). Make sure no other program or kernel module 
(such as sdc2xx, stv680, spca50x) is using the device and you have read/write access 
to the device.

```

What I get from this is that a normal user doesnt have full permissions on the USB device... how can I get this to work without having to resort to digikam with root privileges?

---

### Post by superstoned on 2008-04-06
> **librano said:**
> hi everyone!

I am trying to get my Kodak C300 digital camera working with Ubuntu Edgy. I am able to import photos and movies from the camera when I run digikam with root privileges... everything works fine... however, as a normal user, Ubuntu detects the camera, pops up a dialogue to import the pictures but then comes up with this error

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim
 interface 0 (Operation not permitted). Make sure no other program or kernel module 
(such as sdc2xx, stv680, spca50x) is using the device and you have read/write access 
to the device.

```

What I get from this is that a normal user doesnt have full permissions on the USB device... how can I get this to work without having to resort to digikam with root privileges?
Have a look at the groups your user is member of. Just like the group 'audio' gives access to the soundcard, being in the group 'camera' gives access to camera's... It might also be plugdev or something like that.

---

