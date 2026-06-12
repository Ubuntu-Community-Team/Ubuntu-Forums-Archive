---
title: "Logitech  QuickCam Pro 9000"
date: 2008-05-25
forum: Hardware
---

### Post by Lord Grover on 2008-05-25
Is it possible to get the logitech QuickCam Pro 9000 working in HH? Logitech do not offer drivers and I've installed Cheese with no success.

---

### Post by hotweiss on 2008-05-25
> **Lord Grover said:**
> Is it possible to get the logitech QuickCam Pro 9000 working in HH? Logitech do not offer drivers and I've installed Cheese with no success.

I have this camera, and it works out of the box in Hardy Heron.

---

### Post by linuxwizard on 2008-05-25
Lord Grover

Alot of Logitech webcams will works out of the box. Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

### Post by Lord Grover on 2008-05-26
Unfortunately mine does not.
Ekiga appears to detect the camera but steadfastly refuses to use it.
[QUOTE=Ekiga]Error while opening video device UVC Camera (046d:0990)[/QUOTE]
[QUOTE=Ekiga]Your driver doesn't seem to support any of the colour formats supported by Ekiga.[/QUOTE]
[QUOTE=lsusb]user@host:~$ lsusb
Bus 007 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000[/QUOTE]

---

### Post by linuxwizard on 2008-05-26
Did you work with the setting in Ekiga ? Make sure Video Plugin  shows V4L2. Your webcam > Bus 004 Device 002: ID 046d:0990 Logitech, Inc.  > shows supported here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) . If cam still does not work reinstall the driver.

---

### Post by Roger D on 2008-05-28
I've got a Logitech Pro 9000 and had also had real problems with Cheese - the activity light goes off afte a few seconds. However, I've managed to record videos, with sound, using guvcview: [http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

It's well worth a try.

Roger D

---

### Post by SL666 on 2008-06-02
I've got one of these.. and unfortunately the one thing i want to do with it, seems like a super basic thing, but i can't get seem to get it working.. 

I just want the cam to snap a jpeg of my fish every 30 seconds.. i currently use 'webcam' but it doesn't want to work with the drivers that the pro 9000 uses.. 

anyone have anything that works for this?

---

### Post by yugan on 2008-06-07
> **Roger D said:**
> I've got a Logitech Pro 9000 and had also had real problems with Cheese - the activity light goes off afte a few seconds. However, I've managed to record videos, with sound, using guvcview: [http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

It's well worth a try.

Roger D

thanks broo its working for me..

---

### Post by oluapSissa on 2008-06-09
guvcview can grab pictures pictures every 30 sec if you want :)

guvcview -i image.jpg -c 30

for more options check guvcview --help

---

### Post by oluapSissa on 2008-06-09
Cheese uses the old v4l interface while the linux-uvc driver uses the new v4l2, this is the reason why cheese doesn't work with uvc cameras.
You will need a v4l2 compliant software like luvcview or guvcview.
amsn, ekiga and skype should also work with this camera.

check the following forum for more information:
[http://forums.quickcamteam.net/](http://forums.quickcamteam.net/)

---

### Post by SL666 on 2008-06-09
I did end up getting the 'webcam' software to work, but its unreliable, so i will try guvcview.. 

I get this error (seems only to be when dark?) 

```
v4l2: oops: select timeout
capturing image failed
```

---

### Post by oluapSissa on 2008-06-09
> **SL666 said:**
> I did end up getting the 'webcam' software to work, but its unreliable, so i will try guvcview.. 

I get this error (seems only to be when dark?) 

```
v4l2: oops: select timeout
capturing image failed
```

Never tried 'webcam' myself, but guvcview should work just fine. You can set the file name in the GUI so it will be remembered on the next session this way you wouldn't need the '-i' argument.
File names will be auto numbered if this option is set.

Paulo,

---

### Post by ftmichael on 2008-11-29
Switching the video settings in Ekiga from V4L to V4L2 seems to have fixed the error I was getting there.

Now how do I remove that old UVC driver that I installed quite unnecessarily (a newer version of it is included in the latest kernel)?

---

### Post by chejrw on 2008-12-01
Mine seems to work 'out of the box' for both audio and video in Ekiga, but doesn't play nice with anything else.  I can't seem to record audio in Audacity, and Camorama gives me the dreaded "Could not connect..." error.  Skype picks up the video, but not the audio.

Any help?

---

