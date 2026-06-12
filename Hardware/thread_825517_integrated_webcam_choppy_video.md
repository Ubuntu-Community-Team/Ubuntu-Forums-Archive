---
title: "integrated webcam choppy video"
date: 2008-06-11
forum: Hardware
---

### Post by mo.reina on 2008-06-11
my integrated webcam produces very choppy video, kind of strange considering the laptop is brand new.  i have an ASUS F8SR.

this is the output of lsusb

```
mo@mo-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:5a31  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 08ff:1600 AuthenTec, Inc. 
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

quick google shows that device 002 174f:5a31 is a Sonix 1.3 mega pixel webcam.

anyone know how to configure the camera so that the playback is smooth?  i've already tried installing the uvc driver but it didn't make any difference

---

### Post by linuxwizard on 2008-06-11
Are you using any desktop effects? If so turn effects off or disable them. Then try your webcam see how it works.

---

### Post by mo.reina on 2008-06-11
turned off compiz, webcam still choppy.... is it possible that it's the hardware?  seems kind of strange since it's a brand new laptop and the camera is 1.3 MP...

---

### Post by linuxwizard on 2008-06-12
Which app/program are you using to test your webcam ? Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2.)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

Your webcam > 174f:5a31 Sonix USB 2.0 Camera > shows supported > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > you might check to see if a newer versions of the driver is available and update it.

---

### Post by mo.reina on 2008-06-12
i've been using cheese and skype to test my webcam.  for some reason it doesn't work under ekiga.  also, i only have v4l, not v4l2.  what should i do from here?

---

### Post by mo.reina on 2008-06-12
i've also installed the drivers from the linux-uvc site

---

### Post by linuxwizard on 2008-06-12
After you installed the driver did you reboot your computer and than try Ekiga again ? The Video Plugin setting in Ekiga should give you V4L2 option. Linux UVC driver only supports Video4Linux 2 (V4L2). I don't use Skype so I can not help you there. Not sure what else to suggest you try. Maybe someone else will offer some input.

---

### Post by mo.reina on 2008-06-12
ok, so i've installed ubuntu 8.04, whereas i was using xubuntu 8.04 before.  now the vl42 option is there.  possible discrepancy in the kernel drivers?

---

