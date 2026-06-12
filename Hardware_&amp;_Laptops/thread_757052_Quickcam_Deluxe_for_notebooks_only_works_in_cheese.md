---
title: "Quickcam Deluxe for notebooks only works in cheese"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by Tuxoid on 2008-04-16
I have a Logitech QuickCam Deluxe for Notebooks that for some reason can only capture in Cheese (occasionally). I don't mind Cheese; I just need more features. I have tried to capture with Camorama, but it's unable to connect to video0 (i.e. my webcam). It's incredibly odd to me. I have tried different drivers (uvcvideo, gspca, spca5xx), several different webcam wizards (EasyCam, EasySpca, EasyCam2, EasyToys), and a few different different capture apps (XawTV, Camorama, Cheese, UVCView). UVCView does work but I don't think I can save movies from. I have figured out that the uvcvideo driver is the most compatibility, but still isn't working as I believe it could. I have been trying for hours to get it working. Anyone know why my webcam is only working in Cheese and UVCView, but nothing else?

---

### Post by MetalMusicAddict on 2008-04-16
I have this cam working just fine OTB. 1 BIG thing to remember is to not have it go through a hub. Plug it directly into a port on the computer. Issues like you describe can be caused by a hub. If not, I'm not sure of your issue.

---

### Post by linuxwizard on 2008-04-16
You need the UVC driver your cam is listed here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
Camorama does not support v4l2 that is why you are getting error message.

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Tuxoid on 2008-04-16
> **MetalMusicAddict said:**
> I have this cam working just fine OTB. 1 BIG thing to remember is to not have it go through a hub. Plug it directly into a port on the computer. Issues like you describe can be caused by a hub. If not, I'm not sure of your issue.

I am not on a hub. Just using my built-in ports.

> **linuxwizard said:**
> You need the UVC driver your cam is listed here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
Camorama does not support v4l2 that is why you are getting error message.

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

I see... well, I got Ekiga working. thanks for your help. I just needed to start up ekiga, go through the wizard, take my webcam out of my usb port and while Ekiga was still running, put the webcam back in the computer.

Thank you

---

### Post by linuxwizard on 2008-04-16
You're Welcome Glad that I was able to help you. Good Luck

---

