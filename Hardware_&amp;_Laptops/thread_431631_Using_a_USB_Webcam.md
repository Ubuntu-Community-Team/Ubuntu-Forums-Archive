---
title: "Using a USB Webcam"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2007-05-03
I just jacked in a USB webcam on my Ubuntu desktop machine and I was wondering if any of you guys use a USB webcam in Linux? If so, what do you use in Gnome or KDE to interface with the webcam?

I checked "dmesg" after plugging in the camera and here is what I saw:

```
[231774.983482] Linux video capture interface: v2.00
[231775.012130] pwc: Philips webcam module version 10.0.12 loaded.
[231775.012135] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[231775.012138] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[231775.012141] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[231775.012528] pwc: Logitech QuickCam 4000 Pro USB webcam detected.
[231775.013033] pwc: Registered as /dev/video0.
[231775.165012] usbcore: registered new interface driver Philips webcam
[231775.453085] usbcore: registered new interface driver snd-usb-audio

```

---

### Post by loell on 2007-05-03
you can fire-up ekiga to see it, or install and run camorama and xawtv.

now you can use im/messengers with webcam capabilities :KS

---

### Post by CarlosinFL on 2007-05-03
I don't use IM. I simply want to use it as a ghetto surveillance device for my work cubicle.

---

### Post by CarlosinFL on 2007-05-03
Thanks. Ekiga seems to work fine.

---

### Post by KillerBob-it on 2007-05-03
> **loell said:**
> you can fire-up ekiga to see it, or install and run camorama and xawtv.

now you can use im/messengers with webcam capabilities :KS

Which im with webcam capabilities do you use? I tried aMSN and skype but at now there's no videoconference support for linux.

---

### Post by loell on 2007-05-03
> **KillerBob-it said:**
> Which im with webcam capabilities do you use? I tried aMSN and skype but at now there's no videoconference support for linux.

ekiga, openwengo, kopete, gyachi

and yeah amsn.

---

### Post by jjordan on 2007-05-03
OpenWengo runs great including Video and is much cheeper than Skype.  It is available for Linux, OS X and Windows.   Open Source all the way!  If you just want to see what is on the camera take a look at KDETV, works great for me.

-j

---

### Post by KillerBob-it on 2007-05-03
Actually I mean an IM to have video conference with msn or skype users, since all my friends use those clients... I just downloaded and installed Mercury, later I'll test it ;)

---

### Post by jjordan on 2007-05-03
Hmm, WengoPhone works with MSN but I don't know about Video as I don't know anyone who uses MSN.  Skype will not work with ANY other software as it is proprietary and does not wish to play with others.  WengoPhone will work with others as it uses the SIP standard.  This is still a fairly young software but it is the only thing I have found that allows me to make video calls to my wife.  She uses a MAC and does not want to learn any difficult setups.

-j

---

### Post by KillerBob-it on 2007-05-03
No way to make WengoPhone connecting to the net now... I'll try again later... :(
Anyway it seems what I'm looking for (if it'll work wih video as well ;) )

---

### Post by jjordan on 2007-05-04
I am using the latest 2.1rc2 (rc3 should be out soon).  The one in the repositories is difficult.  2.1rc2 comes with a script that starts it up so you basically unzip it and run the script.

-j

---

### Post by KillerBob-it on 2007-05-05
I downloaded the 2.1 rc2 and now it connects, thank you.
Unfortunately I couldn't have a video conference with a msn user...

---

