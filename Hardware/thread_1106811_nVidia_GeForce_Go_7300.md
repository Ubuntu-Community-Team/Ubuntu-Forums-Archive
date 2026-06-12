---
title: "nVidia GeForce Go 7300"
date: 2009-03-26
forum: Hardware
---

### Post by montauciel on 2009-03-26
Hi everyone, I'm a fresh Linux user, so I hope you will be able to tolerate my lack of knowlege and proper expressions :)

I've searched the boards for this exact issue, but with no luck. 

My system configuration is as following: Lenovo 3000 N200, Core2Duo 2gHz(T7300 I think), 2GB RAM and of course the Geforce Go 7300 which is causing my problems

I'm running Ubuntu 8.10 intrepid ibex

Now, when I activate any of the supported drivers that I'm given in the hardware drivers tab (v.173 or v.177) the title bar in all windows seems to disappear(turn completely white, crossing the borders of the frame) and the overall graphic performance is pretty poor. At the moment I'm not using any drivers and everything seems to be working just fine(without the effects, but it's cool), but I'd like to put up a few games, so I need this damned driver to work:confused: and I'don't like the feeling when I know I'm missing a driver:P

so, if anyone has had the same problem, or has a solution, speak now or forever be silent(or whatever the hell they say on weddings)

Cheers, Vedran

---

### Post by norwoods on 2009-03-26
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by montauciel on 2009-03-27
> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

i added the repository, updated it, but it doesn't show up in SPM..

i'm running a 32bit system

thanx a lot for the help

---

### Post by norwoods on 2009-03-27
> **montauciel said:**
> i added the repository, updated it, but it doesn't show up in SPM..

i'm running a 32bit system

thanx a lot for the help

good old english language; what is the it that doesn't show up, the repository or the drivers?
if you click Origin in the lower left of the Syntactic Package Manager, you should see(above the button):
[www.avenard.org/main](www.avenard.org/main)
[www.avenard.org/multiverse](www.avenard.org/multiverse)
[www.avenard.org/restricted](www.avenard.org/restricted)
if you do not, you have entered the repository incorrectly.
if you click [www.avenard.org/main](www.avenard.org/main), you should see(among others):
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
if you click [www.avenard.org/restricted](www.avenard.org/restricted), you should see:
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
where in this list of actions does your it not show up?

---

### Post by montauciel on 2009-03-27
> **norwoods said:**
> good old english language; what is the it that doesn't show up, the repository or the drivers?
if you click Origin in the lower left of the Syntactic Package Manager, you should see(above the button):
[www.avenard.org/main](www.avenard.org/main)
[www.avenard.org/multiverse](www.avenard.org/multiverse)
[www.avenard.org/restricted](www.avenard.org/restricted)
if you do not, you have entered the repository incorrectly.
if you click [www.avenard.org/main](www.avenard.org/main), you should see(among others):
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
if you click [www.avenard.org/restricted](www.avenard.org/restricted), you should see:
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
where in this list of actions does your it not show up?

sorry, what I wanted to say is that I added the following line:

```
deb http://www.avenard.org/files/ubuntu-repos intrepid release
```

to the repository list

found it under origins, installing now, we'll se how it works

thanx a billion :)

---

### Post by montauciel on 2009-03-27
yep, seems to be working like a dream with the new driver, hope it lasts :D

thanks again

---

