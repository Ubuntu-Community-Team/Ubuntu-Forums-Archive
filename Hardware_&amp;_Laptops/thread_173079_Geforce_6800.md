---
title: "Geforce 6800"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by Slavus on 2006-05-09
Does anyone use a 6800? if so, how did you get your drivers to install?

The latest Nvidia drivers freeze up my system after i install them, ive tried everything, configured xorg.conf, autoconfigured it, compiled my own nvidia kernel, pretty much everything than use an older card

---

### Post by teimu on 2006-05-09
I use one, and it's quite simple if you use the synaptic packages.

in synaptic, type nvidia in the search and you'll get a bunch of results.

you want at least: 
```
linux-restricted-modules-2.6.12-10-386 or later. change 386 if you are using the 64-bit processor ubuntu to 686
nvidia-glx
nvidia-kernel-common
xserver-xorg-driver-nv
```

some of these may be redundant, but its what i use, and it works well.
I remember when i first started installing the drivers from the site, and i also ran into crashes. With these, I havent yet had a video-related crash. These modules may not be the latest, but they are the most stable for ubuntu.

You may also need to tinker around with your /etc/X11/xorg.conf and change 'nv' to nvidia.

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) has a good guide how to do it actually. try that first, then download the other stuff above if you're having problems. follow the instructions of configuring using 'sudo nvidia-glx-config enable' and such.

---

### Post by Slavus on 2006-05-09
Well, considering I have now tried everything one by one, I dont think its my drivers/card thats the problem. Its glx.

when everything is configured properly, either manually or auto, the xorg.0.log always stops at "loading module glx"

with an error: "caught signal 11"

signal 11 is usually a hardware problem, correct? So i am either looking at a new video card, or some way to fix GLX from stopping.

---

### Post by Ozonium on 2006-05-25
[QUOTE=Slavus]Does anyone use a 6800? if so, how did you get your drivers to install?

The latest Nvidia drivers freeze up my system after i install them, ive tried everything, configured xorg.conf, autoconfigured it, compiled my own nvidia kernel, pretty much everything than use an older card[/QUOTE]

I am using a 6800. I downloaded and installed the drivers from the Nvidia site, but it was not sufficient. When I loaded the new module by hand and called startx, it worked, but did not worked on next boot. 

After much testing, I discovered that the nvidia module that Ubuntu loads is built in initrd and mounted in /lib/modules/2.6.12-9-amd64-k8/volatile. Thus, it is necessary to make a new initrd with the new module built in.

But, as the new release of Ubuntu is near, I came with a temporary solution:
I made a script to unload the old module and install the new one:

#!/bin/bash
sudo  cp /lib/modules/2.6.12-9-amd64-k8/kernel/drivers/video/nvidia.ko /lib/modules/2.6.12-9-amd64-k8/volatile/
sudo rmmod nvidia
sudo modprobe nvidia
startx

Thus, when the system boots, the X server cause an error since the module is the old one from initrd. I then call the script above and it starts normally, 2D and 3D working.

I expect that the new Ubuntu release should fix this issue.

---

### Post by tseliot on 2006-05-26
Why don't you try my scripts?
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

