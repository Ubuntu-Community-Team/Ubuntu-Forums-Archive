---
title: "Ubuntu is trying my patience"
date: 2009-01-10
forum: Hardware
---

### Post by dougalkerr on 2009-01-10
I must admit that although I like a challenge, Ubuntu Hardy Heron is trying my patience. I have tried with just a little success to get the correct resolution on my laptop (an ageing Acer Travelmate 630). I have succeeded to get the resolution but, not the NVIDIA driver to work properly. I have tried all sorts of ways to correct the problem but, it looks to me to be a lost cause and I have given up trying to get a clearer desktop at the moment as I can use Ubuntu as is just now and that will do for email and the bog standard stuff.
Now my problem today is trying to get pictures from my digital camera. I am a keen amatuer photographer and have succeeded in installing Picasa to try importing my pictures but, to no avail. It seems something is holding onto the USB ports. I have two on my laptop and both give the same results. Ubuntu cannot capture from the ports even though it correctly identifies my camera.
Any ideas guys?? I desperately need to get something working on this area else my next step will be a new laptop and probably with Windows so that I can at least set up a dual boot with Ubuntu till I can get to grips with Linux and sort out technical problems like this myself!!
Thanks in advance for any kind of help you can give...

---

### Post by ajgreeny on 2009-01-10
Short of adding the resolutions you want to your /etc/X11/xorg.conf file I am not sure if I can help with your resolution problem.
Here's what the appropriate part of mine looks like:-
```
Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```Try adding your own requirements to yours and see if it helps.

For photo imports try f-spot, which is in the repos.  It certainly works for my setup, though I suppose it may differ from camera to camera.

---

