---
title: "Built in webcam not seen/no dev/video0 dir"
date: 2011-11-05
forum: Hardware
---

### Post by lcflwt on 2011-11-05
I have an Acer Aspire AOD255 with an Acer Crystal Eye built in webcam and just went back to 10.04 UNE. 10 months ago I ran this set up and the webcam was plug&play. This time it is not seen by software Cheese nor Skype, No dev/video0 exists. (I do have dev/audio). No icons exist anywhere showing the presence of the camera. I have been searching extensively, mostly in these forums, but cannot find my solution. Please help me make 10.04UNE locate this camera. It is on the hardware compatibility list albeit with a different model number.

.Linux netbook 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

04f2:b044       Acer CrystalEye webcam (Acer Aspire 5535 notebooks)       Chicony Electronics       [IMG]http://www.ideasonboard.org/uvc/ok.png[/IMG]

laurel@netbook:/$ ls /dev/aud*
/dev/audio
laurel@netbook:/$ ls /dev/*vid*
ls: cannot access /dev/*vid*: No such file or directory

laurel@netbook:/$ dmesg | grep uvcvideo
[ 5829.844574] usbcore: registered new interface driver uvcvideo
laurel@netbook:/$ dmesg | grep crystal
laurel@netbook:/$ 

laurel@netbook:/$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by diasf on 2011-11-05
The model number can make a lot of difference, that is, the chip of the camera can be something entirely different.

From the lsusb output, I'm fairly certain your camera isn't supported/recognized. To be honest almost seems like isn't even plugged.... (because the lsusb should show the device and name, even without proper drivers, AFAIK)

---

