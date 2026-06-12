---
title: "Gateway Laptop, headphone jack not working"
date: 2009-08-26
forum: Hardware
---

### Post by simynona on 2009-08-26
I have a Gateway T1628 Laptop and since I updated to Jaunty, the headphone jack doesn't work. I will plug headphones in, and no sound will come out of them or the speakers, but the speakers function normally. I'm pretty sure it's not a hardware problem, because when I boot up in Windows, the headphone jack works normally. I'm wondering if the computer even recognises that the headphone jack exists. Please help.

---

### Post by tommcd on 2009-08-27
Have you tried the basics? Open a terminal and type **alsamixer**. Use the arrow keys to move between the options. And the up and down arrows to change volme levels. Make sure the headphone jack is not muted. Use the "M" key to toggle mute on and off.

---

### Post by simynona on 2009-08-27
Yes, I've tried messing with a bunch of sound options. Every volume option is un-muted and on the max volume.

---

### Post by Wootyeah on 2009-08-28
I fixed mine on my Gateway T-1628 byfollowing this guide from step 5 on down and got it working.

Here is the relevant part of what he did (and it worked for me).

from [http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/]("http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/")

"5.  I downloaded and installed the latest alsa-driver:
sudo apt-get install alsaconf
sudo apt-get install alsa-base alsa-utils
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
tar -xjf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
./configure
sudo make
sudo make install 
6.  This didn&#8217;t seem to make much of a difference, so I looked around and tried a script I found here to download and install the latest snapshot. Again, this first didn&#8217;t seem to make much of a difference. Until I looked at the following list of models:
7.  gedit /usr/src/Alsa-1.0.20/alsa-driver-1.0.20/alsa-kernel/Documentation/HD-Audio-Models.txt
This file reveals the following list of models for STAC9205/9254:

ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron
eapd Keep EAPD on (e.g. Gateway T1616)
auto BIOS setup (default)

Compared to the previous version that shipped with Ubuntu, there are two new entries, eapd and auto now. The eapd (external amplifier power down) option looks quite promising, so back to&#8230; 
8.  sudo nano /etc/modprobe.d/alsa-base.conf
and added the following line:
options snd-hda-intel model=eapd probe_mask=1 position_fix=1

Restart and success! The headphones finally work properly. If you were having similar problems and found this blog in the attempt to find a solution, I hope these steps could help you a bit further in your quest. I can imagine that other headphone issues could perhaps be solved as well, with an alsa-upgrade and adjustments to alsa-base.conf."

8)

---

### Post by simynona on 2009-09-27
It worked! Thank you so much! I never thought I would resolve this problem. You're my hero.

---

