---
title: "ubuntu won't recognize android phone"
date: 2011-02-28
forum: Hardware
---

### Post by gad2103 on 2011-02-28
hello everyone. i'm baffled as to why this is happening but when i connect my phone to my computer via usb cable and mount the usb drive on the phone (its an android galaxy s) i see nothing in Places or in lsusb. i am simply trying to move files between my phone and my computer. USB debugging mode is enabled. any help would be greatly appreciated!

---

### Post by roberj13 on 2011-02-28
Silly Q. You mentioned having USB debugging enabled but after you connect the usb are you actually mounting as mass storage. I'm assuming you are but just so no one has to ask. 

I figure you are since even without mounting you should still be seeing the device in lsusb whenconnected. Also have you been able to connect before or have you never been able to see it?

---

### Post by mr_luksom on 2011-02-28
I can't speak for the Galaxy S, but my Droid 2 can select which 'mode' by dragging the top info bar down after plugging it in. I couldn't see it in lsusb either until I selected USE Mass Storage.

---

### Post by bartman2589 on 2011-02-28
There's another similar thread I just posted to where they mention that the android phone is an MTP device, you should probably install the package mtpfs and mtp-tools and possibly the package qlix (an mtp device manager application), maybe even gmtp (a gui to access mtp devices).

If I'm right the package mtpfs should let you access the device from nautilus and many other file managers.  If not then you should still be able to access it using either qlix or gmtp.

---

