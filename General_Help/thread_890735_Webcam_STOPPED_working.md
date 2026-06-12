---
title: "Webcam STOPPED working ???"
date: 2008-08-15
forum: General Help
---

### Post by nami on 2008-08-15
About a month ago, I managed to get my creative notebook pro webcam working and was making good use of it.  I've not used it for a few weeks and a few days ago I plugged it into the usb port and the webcam's led light didn't come on.  I can no longer use the webcam.

I am assuming it has got something to do with updating ubuntu?

Please help me to get this working again.

Thanks.

---

### Post by blazercist on 2008-08-15
you need to recompile the driver against the latest kernel.

---

### Post by nami on 2008-08-15
> **blazercist said:**
> you need to recompile the driver against the latest kernel.

So I just redo everything I did to get it to work in the first place?  Or do I take other steps.  I'm not good with compiling stuff.

---

### Post by dexter on 2008-08-15
> **nami said:**
> So I just redo everything I did to get it to work in the first place?  Or do I take other steps.  I'm not good with compiling stuff.

If you redo the whole procedure it should work again.

---

### Post by nami on 2008-08-25
> **dexter said:**
> If you redo the whole procedure it should work again.

I did the whole procedure again and this has got the camera led back on again, but when i try to load "cheese" it does not chose anything from the camera???

Please help.

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

