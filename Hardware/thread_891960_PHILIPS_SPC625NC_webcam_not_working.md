---
title: "PHILIPS SPC625NC webcam not working??"
date: 2008-08-16
forum: Hardware
---

### Post by collinge on 2008-08-16
Just bought a PHILIPS SPC625NC webcam but I cant get anything to detect it... the CD-Rom does not work.  What can I do?

---

### Post by linuxwizard on 2008-08-17
Have you tried using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga didn't work post results of the command > lsusb

---

