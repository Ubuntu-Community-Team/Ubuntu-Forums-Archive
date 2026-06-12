---
title: "Help.. I can't get my webcam to work!"
date: 2008-08-17
forum: General Help
---

### Post by collinge on 2008-08-17
I have a Logitech QuickCam E3560, I am able to show it on Cheese, but not online. It only shows on cheese for a moment before the box goes black. Whenever I try to access my cam online, Adobe says it cant find a camera. We bought Logitech specifically because we were told that it worked well with Linux, did we buy the wrong one? What can I do to get it to work?

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If that doesn't work post the results of > lsusb

---

