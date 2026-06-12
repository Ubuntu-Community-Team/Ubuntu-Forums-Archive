---
title: "Webcam troubles"
date: 2008-05-12
forum: Hardware
---

### Post by dlawler on 2008-05-12
So I run a Vaio VGN-C150E, and I never really bothered to check my webcam that's built into the computer when i installed ubuntu (6 months to a year) and it doesn't work. i wouldn't really say not working so much as nothing detects it.

any suggestions?

---

### Post by linuxwizard on 2008-05-12
Have you tried using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

### Post by dlawler on 2008-05-12
ok, it still says that it won't recognize it and no devices are detected.

the command comes out like this:

Bus 006 Device 002: ID 054c:02c1 Sony Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-05-12
This is the driver you need > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)  > your webcam > Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd  > is listed as supported.

---

### Post by dlawler on 2008-05-12
how exactly do you install the driver?

it's probably hard to explain, so is there a website where you can refer me>?

---

