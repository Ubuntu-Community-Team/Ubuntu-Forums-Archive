---
title: "not reading gsm memory"
date: 2012-10-15
forum: Hardware
---

### Post by harun3d on 2012-10-15
Memories and sd cards in Android 2 gsm's could be read by ubuntu with usb cable. You had to confirm the usb connection mode on your gsm, and you could enter the files on your gsm and sd card with ubuntu. For windows you needed kies software to read the files on your gsm.

Now with Android  4, when you connect the gsm to ubuntu with a usb cable, without confirmation you can see the upper files  of your gsm and sd card in the gsm, but you cannot see the content of the files, so it serves for nothing.  There is an option in android 4 for mtp connection and camera connection.  It all works on windows mtp and camera but on ubuntu none of these options make you possible to enter your files.  And now for windows it works directly, you CAN read the gsm files without a program.  

ubuntu says:
"Unable to mount SAMSUNG_Android
Error initializing camera: -60: Could not lock the device"


How can I enter the files on my android 4 gsm with usb cable?

---

### Post by harun3d on 2012-12-11
no one has a solution

I though think this is a serious problem.  many people use smartphones and it cannot be connected anymore with ubuntu system as it was in android 2.  
so the phone cannot be used any more as usb stick, as camera to copy your photos, videos, files, 
no more tethering (internet connection sharing outside )
...

---

### Post by typhoon_tip on 2012-12-11
It is a known bug of libmtp, and who knows when it will be solved:
[https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/1015010](https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/1015010)

What you guys can do is click "affects me" button to elevate the heat.

One workaround exists tough: install UMS application for your smartphone, and use the external card without MTP protocol, then all works. Internal SD card cannot be detected tough.

---

