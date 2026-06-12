---
title: "[How-To] Natty Narwhal on the Asus T91MT"
date: 2011-07-22
forum: Hardware
---

### Post by christophermluna on 2011-07-22
So, I finally got everything that I need working on my Asus T91MT with Natty Narwhal. As a disclaimer, I'm running Ubuntu Classic with cairo-dock rather than Unity, because I like it better, so I don't know if everything works as smoothly with Unity. You are free to try and see.

The good news is that most everything works out of the box. To get the resolution correct, I followed the directions [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Emgd_drivers_.28currently_supported.29") to install the EMGD drivers and **fix the screen resolution**:

```
sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
```

Something to be wary of is your updates. There are times in Synaptic Package Manager where I've had the system try to update the kernel, which I am assuming will break the EMGD drivers. So I manually forced four packages to keep their current version and never update.

The EMGD drivers should fix your resolution, and run video reasonable well if you're not doing a lot else. And you'll get 3D and OpenGL, so you've got all your Compiz effects if you want them. I don't know how to fix the resolution of the Plymouth splash screen on boot, though.

The next thing I wanted to get working was **the microphone**. This was easy. I just ran:

```
alsa-mixer
```

And turned up the gain on the microphone. After that, I tested in Sound Recorder and everything worked fine. Also works in Google Talk.

The two-finger scrolling for the Synaptic Touchpad can be enabled normally through Preferences > Mouse, so nothing fancy here.

The webcam worked out of the box with Google Talk for me, no idea if it works on Skype.

I don't think we've got functional multitouch yet for this hardware, but I've gotten by fine with single-touch easytouch gestures. [s]It would be nice to be able to calibrate the touchscreen, but I don't know how to do that. If anyone does, or knows of a multitouch solution that plays nice with rollbacks on the kernel necessary for the EMGD drivers, you could let me know.[/s] **Update:** To calibrate the touchscreen, do the following:

```
sudo gedit /etc/X11/Xsession.d/98x11-common_touchscreen
```

In the file you have created, paste the following:

```
#!/bin/sh

xinput set-int-prop 9 "Evdev Axis Calibration" 32 300 7900 400 7800
```

Save, reboot, done. Source: [this post]("http://ubuntuforums.org/showthread.php?t=1595220&page=7#post11029012").

Also, I have never tried fiddling with the screen-rotate button. I can see the appeal of it, but I never bothered with it. I just bound a simple gesture to rotate documents in evince.

Anyway, all and all it feels like things are getting close for the T91MT. I hope for multitouch one day in the future, but until then Natty is a fast, robust, completely workable solution.

---

