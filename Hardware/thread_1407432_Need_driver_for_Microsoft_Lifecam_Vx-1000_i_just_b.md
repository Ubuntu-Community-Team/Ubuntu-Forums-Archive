---
title: "Need driver for Microsoft Lifecam Vx-1000 i just bought"
date: 2010-02-15
forum: Hardware
---

### Post by aviramof on 2010-02-15
i just bought this new web cam because my old ones didn't support windows seven i'm 
hopping i can also use this camera on ubuntu how can i get it to work?

i'm using lucid 10.04

thanks in advance.

---

### Post by underquark on 2010-02-15
Don't know about Lucid.

It's listed as working out of the box in Jaunty.
List of Skype webcams [here](https://wiki.ubuntu.com/SkypeWebCams).

It's listed as buggy in Karmic:
Bug report [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460118).

---

### Post by aviramof on 2010-02-15
i tried to download this but no luck:
[http://packages.ubuntu.com/lucid/libv4l-0](http://packages.ubuntu.com/lucid/libv4l-0)

test button don't do anything.

---

### Post by no2498 on 2010-02-17
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
for each 1

get a program to use-see the cam with
cheese and wxcam 1 of the 2 will see the cam
getdeb has wxcam

---

### Post by juan.villa on 2010-02-17
The UVC driver (compiled as a module in ubuntu already) would be the one with the task to support that webcam, but according to the UVC site ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) that device is not supported. That does not mean that it is not actually supported, but rather not OFFICIALLY supported. Good luck!

---

### Post by aviramof on 2010-02-18
thanks i'll try this but at the moment i longer use ubuntu not until 10.04 would be released officialy or at least a gflrx driver be released because without ati driver i can't use ubuntu to see movies and etc in my lct toshiba screen the built in dual
view is making my screen look solorize and pink and impossible to use let's hope 
that the final version would have better support for new and old hardware.

---

### Post by aviramof on 2010-02-27
still need help i can get video but not audio.

---

