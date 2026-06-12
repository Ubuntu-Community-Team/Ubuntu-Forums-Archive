---
title: "webcam in hp"
date: 2008-10-10
forum: Hardware
---

### Post by tintumat on 2008-10-10
how do i activate my webcam on my HP dv9601 laptop

---

### Post by linuxwizard on 2008-10-10
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

