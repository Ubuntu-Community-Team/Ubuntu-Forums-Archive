---
title: "Logitech quick cam communicate"
date: 2008-06-06
forum: Hardware
---

### Post by dublinfireman on 2008-06-06
All,

I have installed the camera drivers, and the light now comes on on the camera so I know it's working, but I am still getting an error that says Could not connect to video device (/dev/video).  I'm lost and I'm not sure where to go next to try and make this work

---

### Post by linuxwizard on 2008-06-06
Are you trying to use Camorama ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by dublinfireman on 2008-06-07
I am getting this error with camorama and ekiga.  I'm not sure where to go next.

---

### Post by lswb on 2008-06-07
Most likely your system has named the camera something different from /dev/video, possible /dev/video0. Try this, with camera not connected, open a terminal and type:

   ls /dev >before
then connect the camera, wait a few seconds, and type

   ls /dev >after

Then type
    diff before after.

You will likely see something like /dev/video0 or /dev/camera0 or something in the output. You can rm before and rm after.

Now when you start your camera viewing program, look for somewhere in the preferences or setting to change the device to whatever was found. 

There are some more precise ways to accomplish this but this method is the easiest for me to describe on this forum.

---

### Post by dublinfireman on 2008-06-07
Here's what I got 

jimmy@jimmy-desktop:~$ diff before after
3a4
> audio1
11a13
> dsp1
44a47
> mixer1
689a693,695
> usbdev1.3_ep00
> usbdev1.3_ep81
> usbdev1.3_ep82
721a728
> video1

---

### Post by lswb on 2008-06-07
OK,

/dev/video1 is your camera. Look for a setting in camorama or whatever program you are using that lets you change /dev/video to /dev/video1. I'm guessing that your camera also has a microphone since I see that you also got the mixer1, audio1, and dsp1 devices after you plugged in the camera. If your viewer also does sound, there will likely be a setting that can be changed to one of these also. If not you may be able to get the audio using a separate program.

I'm not familiar with ekiga, but I know it has a setup program. You man need to run that to change your settings before ekiga will work properly. Good Luck.

---

