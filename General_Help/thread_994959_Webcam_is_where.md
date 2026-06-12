---
title: "Webcam is where?"
date: 2008-11-27
forum: General Help
---

### Post by PCessna on 2008-11-27
Hello,

I recently upgraded to Ubuntu 8.10, Please keep that discussion out of this, and I notied my Panasonic webcam now works with cheese, but I don't know how to tell what device name it's picking my camcorder up as.

The reason is, Is because I want to try to use it to edit, but cheese seems to be the only application that actually sees it, and video works perfectly fine.

It's a Panasonic DV camcorder I'm using in WebCam mode, I'll try to get model later, or if anyone needs it

---

### Post by plucky on 2008-11-27
My webcam is **/dev/video0** which is the norm for webcams.

> The reason is, Is because I want to try to use it to edit, but cheese seems to be the only application that actually sees it,

Do you mean that you want to edit videos downloaded from the camera?
What happens when you connect the camera in normal mode,does the system detect it as a storage device?
Are you connecting it via usb lead?

Post output from a terminal of ```
lsusb
``` with the camera connected and not connected.Also the same when in webcam mode.


Good Luck

---

### Post by HoppingWombat on 2008-11-27
As said above, /dev/video0 is the usual location for webcams. If Cheese is the only program detecting your webcam, open up Cheese and go to Edit -> Preferences -- it will say where your webcam is.

---

### Post by PCessna on 2008-11-27
> **HoppingWombat said:**
> As said above, /dev/video0 is the usual location for webcams. If Cheese is the only program detecting your webcam, open up Cheese and go to Edit -> Preferences -- it will say where your webcam is.

Cheese says:
DVC (/dev/video01)

Yup, that's it.. Now why is Cheese the only program seeing it :(

---

