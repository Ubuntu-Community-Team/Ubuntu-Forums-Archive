---
title: "How enable Suyin webcam?"
date: 2013-07-08
forum: Hardware
---

### Post by DrAlbert on 2013-07-08
Hi
I have a laptop integrated webcam. I know that my webcam worked before. I don't use usually my webcam  but today I wanted to take a picture with it. so I tried kamoso and digikam. but there was no camera. I checked systemsettings>digital camera but there wasn't my camera there too.
lsusb command result:
Bus 002 Device 003: ID 064e:f207 Suyin Corp.
I know this is my camera but I don't know how use it with applications.
I tried command "sudo modprobe  uvcvideo". nothing changed.
what should I do?

---

### Post by DeathByDenim on 2013-07-08
If the driver has loaded succesfully, there should be an entry like /dev/video0 or similar. Do you have that?
Does the command "dmesg" tell you anything with regard to the webcam? How about the file /var/log/syslog?

By the way, system settings -> digital camera is for digital photo cameras, not webcams. Also digikam is for managing photos from digital photo cameras as well. As far as I know it doesn't do webcams, but I admit I don't use digikam often. Kamoso should have worked though.

---

### Post by DrAlbert on 2013-07-09
there is [COLOR=#000000]/dev/video0 there. also [/COLOR]I found nothing usefull in dmesg or syslog but after installing luvcview I found that driver has no problem because luvcview works fine with webcam. is there any configuration file for kamoso? I think I should remove it.

---

