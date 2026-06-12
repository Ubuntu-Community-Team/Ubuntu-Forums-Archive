---
title: "NVIDIA GeForce 9400M Ubuntu 9.04 64bt -rt kernel"
date: 2009-10-04
forum: Hardware
---

### Post by ItsAlwaysSunnyIn... on 2009-10-04
I have had a hell of a weekend trying to get the NVIDIA drivers to work on my DELL XPS Studio 1340. I have been using the real time kernel cause I want to use this to do some multi-track recording. Upon my initial installation of Ubuntu 9.04 64-bit, everything seemed to work great out of the box. However when I connected my Dell 20" LCD monitor I found that it was not detected. Works fine in Vista. So reading around I realized it's an issue with the NVIDIA drivers. I tried everything I could find on these forum. Turns out that only the beta drivers (NVIDIA-Linux-x86_64-190.xx) will support the 9400M. Now I was finally able to install this after realizing that it would only install on the generic kernel (2.6.28-15-generic). It seems to work but one question I have is how do I separate the desktop background for each screen? It just stretches it over both. Not a big deal but still annoying. Now I would really like this to work with the rt kernel so I could run ardour, jack, hydrogen, etc.. efficiently. Does anyone have any suggestions? Should I reinstall with the 32-bit? Ubuntu Studio??

Btw, when I attempt to install the drivers on the rt kenerl I get:

"ERROR: Failed to build NVIDIA kenerel"

Since it is installed and running on the generic kernel, i tried just booting up in rt and it doesn't work. I get something like this:
"Ubuntu is running in low-graphics mode, NVIDIA: Failed to load the NVIDIA kernel module..."

Please provide some help if you can. I'm pretty new to all this so excuse my lack of Ubuntu vocab.

---

### Post by ItsAlwaysSunnyIn... on 2009-10-06
Any ideas why my NVIDIA Drivers won't work when I boot up the real time kernel??

---

### Post by motin on 2009-10-19
I've got a XPS 1330 and I am struggling with this too. 

From the hours of investigation so far it seems that Nvidia is not making their drivers for nothing than the generic kernel flavor. the 185 drivers included in Karmic will build, however the resulting drivers are extremely unstable when running the rt kernel (the system _will_ freeze within 1-20 min after boot, and directly when running something like glxgears)

The only way so far I can use the rt kernel is to move my xorg.conf file and reboot into rt. Then when I am done I move it back and boot into generic kernel. But this sucks and is not how I want it to be... 

Still investigating, tell me if you find a solution!

Cheers

---

### Post by motin on 2009-10-19
Suggestion that nvidia beta 190 drivers might work: 
[http://www.nvnews.net/vbulletin/showthread.php?t=138651](http://www.nvnews.net/vbulletin/showthread.php?t=138651)

And instructions: 
[http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html](http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html)

A thread where someone seems to be happy with their 2.6.31 kernel WITHOUT the RT patch: [http://www.linuxmusicians.com/viewtopic.php?f=6&t=2246](http://www.linuxmusicians.com/viewtopic.php?f=6&t=2246)

Bug report about freezing ubuntu studio: 
[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/366352)

Specific to Nvidia (where interesting activity is seen):
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296)

Choosing different drivers on startup depending on kernel used:
[http://ubuntuforums.org/showthread.php?t=1287967](http://ubuntuforums.org/showthread.php?t=1287967)

The official Ubuntu Studio testing thread with interesting conversations:
[http://ubuntuforums.org/showthread.php?t=1241103](http://ubuntuforums.org/showthread.php?t=1241103)

---

