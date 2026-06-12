---
title: "Sound comes out of both internal speaker and jack"
date: 2011-11-30
forum: Hardware
---

### Post by 3rlend on 2011-11-30
Hey I've had this issue for a while! Using Ubuntu 10.04. Didn't have the problem on 11.04, but I dislike that version.

When I plug in my jacks, the sound comes out of both internal speakers and the jack. If I go to System -> Preferences -> Sound and change audio output from* Internal Audio Analog Stereo *to *RV710/730 Analog Stereo (HDMI)*, then no sound comes out of neither internal speaker and jack!

Please help me, thank you very much!

---

### Post by /dev/random/username on 2011-11-30
The way i fix it on my machine CentOS I edit /etc/modprobe.d/dist-alsa.conf
and add

> options snd-hda-intel enable_msi=1

I hope its the same on Ubuntu.

---

### Post by 3rlend on 2011-11-30
> **/dev/random/username said:**
> The way i fix it on my machine CentOS I edit /etc/modprobe.d/dist-alsa.conf
and add



I hope its the same on Ubuntu.

In ubuntu there's a file alsa-base but that's the closest. Also, I can't edit it because it's read only :/

---

### Post by /dev/random/username on 2011-11-30
Use sudo

sudo nano /etc/modprobe.d/alsa-base.conf

---

### Post by 3rlend on 2011-11-30
> **/dev/random/username said:**
> Use sudo

sudo nano /etc/modprobe.d/alsa-base.conf

Okay I tried both that and the one at this page [http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html](http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html) but none worked.
Do I need to restart or something?

---

### Post by /dev/random/username on 2011-11-30
I always restart when I enable_msi

---

### Post by 3rlend on 2011-11-30
> **/dev/random/username said:**
> I always restart when I enable_msi

Ah thanks IT WORKS! THANK YOUUU! :D

---

### Post by /dev/random/username on 2011-11-30
I'm glad i could help you.

---

