---
title: "Tips for Creative Live! Cam Chat problem?"
date: 2009-11-06
forum: Hardware
---

### Post by [matt] on 2009-11-06
I am attempting to run a Creative Live! Cam Chat webcam on Ubuntu 9.10 (for Skype). I have plugged the cam in and under "select webcam" in the drop down menu it says that no webcam has been detected. I have looked over the supported and unsupported webcam list and this EXACT model isn't shown. I am considering trying some troubleshooting with drivers to get this working. Any recommendations on the most likely drivers/methods to work with this cam?

Thanks...

---

### Post by [matt] on 2009-11-08
Ok, my cam has mysteriously started working, sorta. 
I happened to notice today that the red light was illuminated on my cam. I started Skype and went into the video preferences. It showed a name for my device(before it told me that there were no supported devices on my system). As soon as I clicked the "test video" button, the red led light went out and I got some kind of garbed green image. I started Cheese and VLC and they are both now displaying the cam video perfectly. I read the Ubuntu documentation on webcams and it mentioned changing the way Skype launched to solve this problem:

> Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with  

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'I tried this with no apparent change in behaviour in Skype. I have read about the hacked ov51x jpeg driver and it claims to support my camera(the usb lds:041e:405f matches up). So should I try to install this driver hack thing when I obviously have a driver installed that works just fine? It seems to be a problem with Skype? Any suggestions?

---

### Post by gordintoronto on 2009-11-08
Cams are a mystery.  Yesterday my grotty Z-Star ZC0303 webcam wouldn't work in Skype under Linux Mint Gloria or (ahem) Windows Live Messenger under Windows 7.  Today it does.  Perhaps the difference is that I ran Cheese and have not turned off the power.  (I'm suspicious that Cheese somehow initializes the camera and the other programs benefit from it.)

Or maybe it's something else entirely.

---

