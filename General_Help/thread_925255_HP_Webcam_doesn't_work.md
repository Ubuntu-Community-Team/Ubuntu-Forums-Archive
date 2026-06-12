---
title: "HP Webcam doesn't work"
date: 2008-09-20
forum: General Help
---

### Post by Prominence on 2008-09-20
How can I get it to?

---

### Post by linuxwizard on 2008-09-20
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by Prominence on 2008-09-20
Bus 007 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-09-21
I don't see a webcam listed. Normally HP uses a Microdia or Ricoh webcams.

---

### Post by Prominence on 2008-09-21
It worked under aMSN. Nothing else can see it or use it.

---

