---
title: "Need help with webcam drivers. (chicony icam 6120)"
date: 2008-07-11
forum: Hardware
---

### Post by fiddledeedee on 2008-07-11
Where could i get webcam drivers? 
Webcam: chicony icam 6120
lsusb:
```

Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 093a:2608 Pixart Imaging, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

Thanks in advance.

---

### Post by linuxwizard on 2008-07-12
Alot of webcams will just work out of the box. Have you tried using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

