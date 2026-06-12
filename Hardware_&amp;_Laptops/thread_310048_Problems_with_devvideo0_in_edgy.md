---
title: "Problems with /dev/video0 in edgy"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by pranjan on 2006-11-30
Folks:
 I am having issues with edgy where my usb webcam in laptop (DELL XPS M1210) is not being detected. In fact /dev/video0 itself doesn't exists. 
 > uname -a
Linux sone 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
>lsusb
Bus 005 Device 003: ID 046d:08c6 Logitech, Inc. 
:???:

---

### Post by scooper86 on 2006-12-23
Here is a good link I found when getting the camera to work on my dell xps m1210
[Debian Wiki]("http://wiki.gacq.com/index.php/Installing_Debian_on_Dell_M1210#WebCam") if youve sorted this already cool but just incase someone else needs it here it is:

basically

```
sudo apt-get install subversion
```

```
cd /usr/src
```

```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/
```

```
cd linux-uvc/linux-uvc/trunk
```

```
sudo make
```

```
sudo make install
```

```
modprobe uvcvideo
```

To make the drivers load at boot

```
sudo nano /etc/modules
```

And add uvcvideo to the list of modules

Then either use the software the guy on the above link uses or something like kopete or skype.

---

### Post by dbglt on 2007-02-12
I have the same issue. I have installed the driver (and mobprobing it causes no issues at all).

This camera *IS* supported - many others have got it to work, but for some reason it is not being detected, and thus no device /dev/video is being created.

On a "modprobe uvcvideo", my dmesg reads:

```

[24666.260000] Linux video capture interface: v2.00
[24666.336000] usbcore: registered new interface driver uvcvideo
[24666.336000] USB Video Class driver (v0.1.0-c)

```

It  fails to actually find and initialise the device (It should have another line "found compliant blah blah..."). I know the webcam on this machine works (it works fine in windows), and I know others have got it to run. I can't for the life of me see what is missing - this is not covered in any documentation, whatsoever.

Something odd is going on, and it may be to do with edgy, or perhaps even my setup, as far as I can tell. Anyone able to shed some light?

---

### Post by onedem on 2007-03-19
0.1.0-c from ubuntu deosn't work, but 0.1.0 from svn.berlios.de does.

---

