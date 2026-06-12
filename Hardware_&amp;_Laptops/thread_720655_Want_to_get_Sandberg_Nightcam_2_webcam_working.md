---
title: "Want to get Sandberg Nightcam 2 webcam working"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by pinkunicorn on 2008-03-10
I have a Sandberg Nightcam 2 webcam that I'd like to get to work. 

When I plug it in, I get this in /var/log/messages:
```
Mar 10 17:34:51 localhost kernel: [468063.408000] usb 4-6: new high speed USB device using ehci_hcd and address 14
Mar 10 17:34:51 localhost kernel: [468063.540000] usb 4-6: configuration #1 chosen from 1 choice
```

I'm told on [http://www.andersjensen.dk/wordpress/?cat=10](http://www.andersjensen.dk/wordpress/?cat=10) [in Danish, which I can understand] that this camera should work with the spca5xx driver. Technically it says that a "Sandberg Nightcam" works with that driver, but that's the closest thing to my camera that I've managed to google up anything at all for, so for the moment I'm going to assume that it will use the same driver unless someone knows for a fact that it won't.

Armed with information about what driver I need, I try to install that```
hasse@orangutan ~/config :-) apt-cache search spca5xx
gspca-source - source for the gspca v4l kernel module
spca5xx-source - source for the spca5xx driver
```
but only find source modules. If possible, I'd like to avoid installing from source or at least without instructions.

Through a forum search, I also find my way to [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx) which tells me at the top of the page that Dapper and later versions come with spca5xx preinstalled. When I scroll down to "Troubleshooting", however, it tells me that the driver may still need installing and points me to [http://scottabbey.org/node/12](http://scottabbey.org/node/12) for instructions. This sounds great, but the link is broken. Or, rather, it points to a page which doesn't contain any driver installation instructions at all.

This section also tells me that I should get a /dev/video or /dev/video0 device when my camera is plugged in if everything is correctly installed. I get neither. My camera is connected directly, not via a USB hub.

Any help on how to get this camera working is appreciated.

---

### Post by linuxwizard on 2008-03-10
What app. have you used to see if cam works ? It may just work. Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If that does not work post results of the command > lsusb

---

### Post by pinkunicorn on 2008-03-10
I assumed that if I wasn't getting a /dev/video or /dev/video0, nothing else would work either.

I've now tried ekiga, and it says that it can't find any video devices.

lsusb gives me this:```
Bus 004 Device 015: ID 0c45:627b Microdia 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 011: ID 046d:c012 Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000  
```

The first line is the camera (verified by unplugging the camera and testing again).

---

### Post by linuxwizard on 2008-03-10
For Microdia webcam you can get drivers here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by intel on 2008-03-12
please join the user support group for microdia webcams here

https://groups.google.com/group/microdia

---

### Post by pinkunicorn on 2008-03-13
> **linuxwizard said:**
> For Microdia webcam you can get drivers here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

I've installed the driver but it doesn't seem to have any effect.

The only thing I get in /var/log/messages is still ```
Mar 13 20:57:12 localhost kernel: [ 1281.168000] usb 4-6: new high speed USB device using ehci_hcd and address 3
Mar 13 20:57:12 localhost kernel: [ 1281.300000] usb 4-6: configuration #1 chosen from 1 choice
``` and Ekiga still claims that there is no video device.

---

### Post by linuxwizard on 2008-03-13
I don't know much about that driver. All I know is people with Microdia webcam use that driver some cams works and some don't. Not sure if it will matter or not did you uninstall that other driver you installed for your cam ? You want to make sure the webcam is not still trying to use the spca5xx driver. Try this should show which driver your cam is using >  lsmod | grep videodev

---

### Post by pinkunicorn on 2008-03-13
> **linuxwizard said:**
> Not sure if it will matter or not did you uninstall that other driver you installed for your cam ? You want to make sure the webcam is not still trying to use the spca5xx driver. Try this should show which driver your cam is using >  lsmod | grep videodev

It seems to use neither gspca or spca5xx:```
hasse@orangutan ~ :-) lsmod | grep video
videodev               28288  0 
v4l2_common            17536  1 videodev
v4l1_compat            14468  1 videodev
video                  17164  0 
```

I didn't deinstall anything manually, but when installing the driver deb there was a question about whether to remove another driver (which I said was OK), so I assume the installation did that. Unfortunately I don't have the exact message saved.

---

### Post by linuxwizard on 2008-03-13
The driver name will appear on the line starting with "videodev". Did you reboot your computer after installing that driver ? If not try that and see what happens.

---

### Post by pinkunicorn on 2008-03-13
> **linuxwizard said:**
> The driver name will appear on the line starting with "videodev". Did you reboot your computer after installing that driver ? If not try that and see what happens.

The line starting with "videodev" doesn't have any name on it at all (as can be seen in my previous post).

I have rebooted, both with and without the camera connected, but it doesn't make any difference.

---

### Post by linuxwizard on 2008-03-13
Yes I know that their were no driver name listed. Not sure if you found this on the website > [http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6) > but I don't see your cam listed as supported.

---

