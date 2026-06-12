---
title: "LogiCool Cam not working?"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by XANA on 2008-02-22
Hello all,

I have a problem with my newly purchased LogiCool (Web)Cam.
It is detected as **_/dev/video0_**, but no application can connect to it (except Camera Monitor, but I disabled CM and no difference)

Apparently, the camera seems to turn itself off when no program's using it and when the WebCam is  unplugged it stays off (the button on the top is not the PW  button either); I don't know how to re enable it either

Any help is appreciated,
X.A.N.A.

---

### Post by linuxwizard on 2008-02-22
Which application have you tried ? Try using Ekiga to see if cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If you have already tried does not work > post results of the command > lsusb

---

### Post by XANA on 2008-02-22
>START OF LSUSB OUTPUT<
Bus 005 Device 012: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 013: ID 058f:6362 Alcor Micro Corp. 
Bus 005 Device 007: ID 0930:6540 Toshiba Corp. 
Bus 005 Device 004: ID 1307:0163  
Bus 005 Device 006: ID 047d:105e Kensington 
Bus 005 Device 005: ID 058f:6254 Alcor Micro Corp. 
Bus 005 Device 002: ID 058f:6254 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
**_Bus 001 Device 004: ID 046d:08ae Logitech, Inc. <<<This is the webcam>>>_**
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000   
>END OF LSUSB OUTPUT<
It is detected in lsusb and ekiga.
but i tried to access it in ekiga and it gave me this:

>START OF ERROR<
Error while opening video device /dev/.static/dev/video0

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded.
>END OF ERROR<

I looked in Synaptic and downloaded any thing that popped up in my search ("webcam"), none of those programs were able access the cam.
XSANE came very close to accessing it, the only error message it gave was the "invalid argument" one.

---

### Post by linuxwizard on 2008-02-22
Did you try working with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices >  Try > Video Plugin > V4L > Input Device > click on see if your cam shows up in drop down menu > click on Detect Device.

XSANE is for scanners.

---

### Post by XANA on 2008-02-22
> **linuxwizard said:**
> Did you try working with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices >  Try > Video Plugin > V4L > Input Device > click on see if your cam shows up in drop down menu > click on Detect Device.

XSANE is for scanners.

First: Yes I tried with v4l and v4l(v2). It is detected and seen in Ekiga as /dev/.static/dev/video0
I can't get it to access the cam as it will pop up the error I showed you
(See section beginning with ">START OF ERROR<")

Second: Yeah I know but XSANE Does Detect my logicool camera....It even shows up a second window with the name of my camera there in the title bar!
And I tried running XSANE again, no dice (it tries to find the camera, but says no device found)

The camera is ON (the green light is ON) and i can find it in /dev/video0 but NOTHING (not even Camera Monitor now) can access it!

---

### Post by linuxwizard on 2008-02-23
Alot of the Logitech webcams just works out of the box. Here is your cam listed 1/2 way down this page > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html). The only thing I can say is to try install the driver, it mightbe a newer version than you have now. Good Luck

---

### Post by XANA on 2008-02-23
Well I looked on the site and it is listed as "YES" (so it is supported fully) and the drivers....
I searched for them in Synaptic and it came up as a source package, which installed perfect (along with the dependiencs for source packages).

The question now is: How do I compile the source package I've installed to the system?

EDIT: I just now tried to access it through the terminal (command prompt) and:
Without SUDO in the space before qcam...It said /dev/video0- Permission Denied
it failed with sudo before it too, just with a different message

I checked my User Account Permissions and they are all checked

---

