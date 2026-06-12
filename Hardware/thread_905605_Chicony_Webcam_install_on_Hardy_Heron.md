---
title: "Chicony Webcam install on Hardy Heron"
date: 2008-08-30
forum: Hardware
---

### Post by mccloudm on 2008-08-30
I have been trying for 2 days now to get this to work. I have installed Camorama Webcam viewer. I have read some stuff on Linux UVC and followed the directions in there wiki but I still can't get this to work. here is my lsusb console readout.

```
Bus 005 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

 I have also done everything to complie this driver listed here. [http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS](http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS)  Still nothing. I can't seem to get the webcam to work. The error that Camorama gives me is  *could not connect to video device (/dev/video0) Please check connection..*. Now I am stuck and don't know what to do.

---

### Post by Crafty Kisses on 2008-08-30
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by IntuitiveNipple on 2008-08-30
Please report the output of:
```

udevinfo --query=all --name=/dev/video0 --attribute-walk

```
and
```

modinfo uvcvideo

```

---

