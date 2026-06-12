---
title: "Need help installing web cam (motion eye, sony)"
date: 2008-08-25
forum: Hardware
---

### Post by tomd123 on 2008-08-25
I have a vgn-fe880e sony vaio laptop. My webcam doesn't seem to be working even after installing the right drivers and checking in cheese. I followed [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation) and did the manual compile, but after I restarted, cheese didn't show anything at all. lsmod revealed that the r5u870 driver was loaded. I have a 
05ca:1836 	Sony Visual Communication Camera VGP-VCC4 	VAIO FE
which is supported by the driver. Any help would be appreciated..:confused:

---

### Post by IntuitiveNipple on 2008-08-25
One of my Vaio laptops has the same Motion Eye camera:
```

$ lsusb
Bus 005 Device 004: ID 05ca:1836 Ricoh Co., Ltd 

```
It works perfectly with the r5u870 driver. I've already packaged it as r5u870-dkms.

I'd suggest you unload and delete the r5u870 you've built so it doesn't confuse the issue, and then download and install the r5u870-dkms package:

I'll repeat here the instructions I gave in another thread earlier:

I help maintain the r5u870 driver and it is [available from my PPA as r5u870-dkms](https://launchpad.net/~intuitivenipple/+archive?field.name_filter=r5u870&field.status_filter=published).

The package uses DKMS (Dynamic Kernel Module Support) - what this means is that the driver is automatically rebuilt by the DKMS system on the PC if the kernel is upgraded. Without DKMS a new binary driver would need to be built and installed each time the kernel was updated.

Fetch and install the r5u870 driver (for Hardy):
```

wget http://launchpadlibrarian.net/16745481/r5u870-dkms_0.11.1-0ubuntu1%7Eppa1h_all.deb
sudo dpkg -i r5u870-dkms_0.11.1-0ubuntu1~ppa1h_all.deb

```

You might have problems at boot-time with the uvcvideo and r5u870 drivers *arguing* over which should manage the camera. In that case, to manually sort it out, unload both drivers then load r5u870 first:
```

sudo modprobe -r r5u870
sudo modprobe -r uvcvideo

sudo modprobe r5u870
sudo modprobe uvcvideo

```

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by IntuitiveNipple on 2008-08-25
For general information: the r5u870 is a V4L2 (Video4Linux 2) driver, the same as uvcvideo.

---

### Post by tomd123 on 2008-08-26
Ok so Ekiga does work with the webcam, but cheese is still showing nothing, except the screen with the color bars and static. Any ideas? Since there is no configuration for cheese, I don't know if it might have a text config. Any help?

---

### Post by tomd123 on 2008-08-26
Nevermind, the manual said to post a bug report if it worked in gstreamer-properties but not in cheese.

---

### Post by Vinnie57 on 2008-11-27
I've had the exact same problem with my PCG-TR3A as tomd123 mentioned. The webcam is a VCC-U01 so no drivers appear to be available. Would hope one can be found or should I just purchase another?  (Running Ubuntu 8.10 and all works wonderfully)
Thanks in advance for any help or direction....

---

### Post by vial89 on 2009-07-11
Hi
I have the same problem, i'm using a vaio pcg-tr3a, I tryed with ekiga and nothing happened
My lsusb is:

Bus 004 Device 003: ID 054c:014d Sony Corp. Memory Stick Reader/Writer
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by cdoebbler on 2009-07-13
Same problem. Can't find driver for camera:

Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera

---

