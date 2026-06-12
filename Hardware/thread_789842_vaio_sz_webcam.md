---
title: "vaio sz webcam"
date: 2008-05-10
forum: Hardware
---

### Post by pengko.eo on 2008-05-10
Hello there ubuntu users all around the world. I tried install ricoh to get my webcam work. Unfortunately no success. I need help. Does anyone know how to get a vaio sz webcam works on hardy heron? Thanks a lot for the help.

```
Bus 005 Device 007: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 005: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 003: ID 054c:0281 Sony Corp. 
Bus 005 Device 002: ID 058f:6254 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by linuxwizard on 2008-05-11
Is this the driver you installed > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) > your cam is listed as supported > [http://wiki.mediati.org/Supported_Devices](http://wiki.mediati.org/Supported_Devices) > 

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by pengko.eo on 2008-05-11
thanks man. its working. this help me a lot

---

### Post by linuxwizard on 2008-05-11
You're Welcome Glad that I was able to help you and you now have your webcam working. Good Luck

---

