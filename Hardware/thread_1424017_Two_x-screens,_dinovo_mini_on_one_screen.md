---
title: "Two x-screens, dinovo mini on one screen?"
date: 2010-03-07
forum: Hardware
---

### Post by jonasback on 2010-03-07
Hello!

I'll start by explaining my setup and then we'll come to my question.
I've connected my computer to my tv with a HDMI-cable. (Sound and video) I've set up my computer to automatically fire up XBMC Media Center on the tv-screen when i start my computer. 

I've got a NVIDIA 9800GTX graphics card, and in the Nvidia controlpanel I've set up my monitor and tv to use "separate x screen". The issue with xbmc is that it locks the mouse and keyboard so it can't be used on my primary monitor. I've solved this by using this script to start it.

```

#! /bin/bash

STATUS=0
WINCLASS=xbmc.bin.xbmc.bin
DISPLAY=:0.1
SLEEPDELAY=1

/usr/bin/xbmc "$@" & 

while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
done

wmctrl -x -r $WINCLASS -b toggle,fullscreen

```

Right now I'm controlling my XBMC with my HTC Hero phone, on wich I've installed [android-xbmcremote](http://code.google.com/p/android-xbmcremote/). However, my girlfriend does not have a androdbased phone, nor an iphone so she can't control anything. :D But controlling the program with my phone has been a little annoying. If I e.g. watch something for a while, and want to watch something else (this applies to music aswell) the phone has dropped the connection to save battery and need to reconnect every time. It takes about 10-15s every time.

I've come up with the solution to by a minikeyboard ([diNovo Mini](http://www.logitech.com/index.cfm/keyboards/keyboard/devices/3848&cl=us,en)). 

**So now to my question:**

Is it possible to lock the diNovo Mini to the 2nd x-screen? That is, when I start my computer and XBMC fires up, the bluetoothconnected keyboard will only work on my tv-screen to control the mediacenter.

---

