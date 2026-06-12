---
title: "[SOLVED] /dev/video assignments for webcams"
date: 2008-10-19
forum: General Help
---

### Post by werries on 2008-10-19
I just spent a good hour wrestling with my computer to get the usb webcam not detected as a soundcard at boot. And heres the situation:

I have both an integrated logitech webcam with a dell xps m1210, but that is broken but still being detected at ```
Bus 005 Device 005: ID 046d:08c6 Logitech, Inc.
``` This is from "lsusb".
Now, the usb webcam is being detected at ```
Bus 001 Device 004: ID 046d:08b1 Logitech, Inc. QuickCam Notebook Pro
```
The integrated is being mounted at /dev/video0, and the usb one at /dev/video1.
In order to use stickam live feed, it needs to be at /dev/video0, for some reason.

Any solution as to change the order, or forcing stickam to use the other. (which i cannot select in flash options but works everywhere else.)
Maybe theres a firefox option I can use?

I'm an intermediate linux user, but I'm completely lost here.

---

### Post by loell on 2008-10-19
if i'm not mistaken the latest flash version can let you select /dev/video[COLOR="Red"]*[/COLOR] , or I could just be immagining. :)

---

### Post by patrickballeux on 2008-10-19
Did you tried Flash 10?

Also, you can right-clik on the Flash applet, and select the webcam to used.  
(Right-Click: Parameters, then last tab...)

There is no need to reorder your webcams...

---

### Post by werries on 2008-10-19
I did try that, doesnt show up...and I have flash 10, downloaded like a week ago.

---

### Post by patrickballeux on 2008-10-19
> **werries said:**
> I did try that, doesnt show up...and I have flash 10, downloaded like a week ago.

Ok, then it seems that Flash (v10) is not able to recognize your webcam.  This can happen on some model (You could report that on the Adobe Lab Site).

It is not about reordering your webcam,  it is simply not detected by Flash (why?  I don't know).

Is it working in Cheese or using "gstreamer-properties" (from command lime or ALT-F2)?

If it is, then you could use WebcamStudio for GNU/Linux and broadcast using the virtual webcam.  Bonus: Special Effects, Text overlay, Multiple webcams supported at the same time.

See my signature for the project link.

---

### Post by werries on 2008-10-19
Yeah, it works fine in cheese, vlc, and skype. I'll check out WebcamStudio. Thanks.
And also, to note, the webcam light flashes on both when stickam is started, and then it chooses the integrated one. So...yeah.

---

### Post by patrickballeux on 2008-10-19
> **werries said:**
> Yeah, it works fine in cheese, vlc, and skype. I'll check out WebcamStudio. Thanks.
And also, to note, the webcam light flashes on both when stickam is started, and then it chooses the integrated one. So...yeah.

Flash is scanning your webcams, and uses the last one you selected.  But (like the EyeToy webcam) some does not work (Mine is showing in the list but gives a black screen).

The fun thing about WebcamStudio is that you will be able to broadcast your 2 webcams at the same time, side by side or in a picture-in-picture mode.  This is fun when you want to show people something in a close-up but still see you at the same time.

And also, it is useful for those webcams not directly supported by Flash, as the EyeToy.  (See my BlogTV link to have an overview of the possibilities).

---

### Post by werries on 2008-10-19
I can get the webcam to show up and be used fine in WebcamStudio, but at the bottom right with the webcam icon, it says "No devices Found" for options, and I can't start the virtual cam. :(
edit: OOPS! didnt modprobe vloopback

---

### Post by patrickballeux on 2008-10-19
> **werries said:**
> I can get the webcam to show up and be used fine in WebcamStudio, but at the bottom right with the webcam icon, it says "No devices Found" for options, and I can't start the virtual cam. :(
edit: OOPS! didnt modprobe vloopback

Read the wiki page "Installation" because you need to install the "vloopback" module which enables the virtual webcam.  Once compiled and installed, you will have the output device needed.

WebcamStudio is by itself only a video mixer.  But it needs to output to a virtual device (vloopback module).

To install that module, download the source file in the libraries (Download - Library - VLoopback) (If you are using Ubuntu 8.10, pick the 1.1.3 version as 1.1.2 will not work, if not, then you can still pick 1.1.3, but 1.1.2 is more stable).

Make sure that you have installed: build-essential and linux-headers-generic to be able to compile the source.


Saddly, vloopback is not part of the repositories, or any other way to create a virtual webcam device.

Good luck!

---

### Post by werries on 2008-10-22
Its all set up and works just fine with stickam. Thank you, this program is great. :)

---

### Post by EvilTchnlgy on 2008-11-16
Just so you know, it isn'tnoted anywhere that webcamstudio has to be run as root. I spent like an hour trying to figure out why I couldnt get the cirtual webcam to work until it dawned as being something as simple as running the program as root... Thanks though. this helps so much

---

### Post by xfearxnxloathing on 2009-05-03
> **EvilTchnlgy said:**
> Just so you know, it isn'tnoted anywhere that webcamstudio has to be run as root. I spent like an hour trying to figure out why I couldnt get the cirtual webcam to work until it dawned as being something as simple as running the program as root... Thanks though. this helps so much

how do you run this as root because i think that is my problem..

---

