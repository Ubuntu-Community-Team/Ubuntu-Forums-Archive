---
title: "Canon 400D - Cannot import photos"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by endtroducing on 2007-03-10
After dist-upgrade, I cannot import photos from my camera. :( 

This is the message I get: 

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I did not check which packages where being upgraded. Is there a log file I can look at?

I checked:  /etc/udev/rules.d/45-libgphoto2.rules

The entry for my camera is there.

(previous post: [http://ubuntuforums.org/showthread.php?t=375010&highlight=xti](http://ubuntuforums.org/showthread.php?t=375010&highlight=xti))

I have restarted the camera, restarted the udev service.

Any help will be appreciated!

---

### Post by larini on 2007-03-10
You must downgrade libgphoto2-2 and libgphoto2-port0 to version 2.2.1 (assuming you are using edgy)

---

### Post by endtroducing on 2007-03-11
Im using Edgy. Downgraded both packages. Same problem... I think I broke something else for my torrent client (azureus) crashes as soon as I launch it... I don't feel like wasting time so i'll backup and do a clean install. Thanks for your help!

---

### Post by rko618 on 2007-03-13
no need to downgrade your libgphoto packages.  The fix is described here:

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

Hopefully that will work for you.

---

### Post by cnbiz850 on 2007-03-13
> **rko618 said:**
> no need to downgrade your libgphoto packages.  The fix is described here:

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

Hopefully that will work for you.

Greaaaaaaaaaaaaaaaaaaaaat!!!!!!!!!!!!!

---

