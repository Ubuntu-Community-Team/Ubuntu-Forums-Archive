---
title: "how to mount usb pendrive?"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by isaac on 2005-02-25
hi,

     My usb pen drive as automatically mount when i boot my ubuntu with gui in it. but  I have no idea how to mount this device when I was running a none GUI ubuntu (server) 

    When I plug the usb pen drive into the usb port.. there's a text written
"sda: assuming drive cache: write through"
  

    what does that suppost to mean? I have tried to look for it with under the following command:

 #cd sda0
#cd /sda0

    By default 2.6.8.1-3-386 kernel which installed with ubuntu should have the usb module compile right? the same kernel version was used for the ubuntu with gui version..

    Can anyone help me out how to mount the usb pen drive?

thanks in advance

---

### Post by acascianelli on 2005-02-25
mount /dev/sda1 /media/usbstick

/media/usbstick can be anything you want it, thats the mountpoint it can be any folder.

---

