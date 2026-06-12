---
title: "Ubuntu 10.10 - Sound card not detected anymore"
date: 2010-09-10
forum: Hardware
---

### Post by feardotcom on 2010-09-10
Ok, im having a problem with my sound card. Here's what happened. I just got a new monitor/tv for my computer (widescreen) and i was trying to get Quake 4's video setting just right and i launched and exited the game about 2 or 3 times. The last time after i get the video settings i noticed quake 4 wasn't playing sound any more and i i figured it was the infamous idtech 4 linux sound issue again. After i exited i noticed the sound icon had the "--" and usually means its been muted. So i click on it and find out i have no sound controls so i go to the sound preferences to find out that my sound card doesn't even show up. I rebooted about 2 or 3 times to see if it would start working, no go. 

I booted into 10.4.1 live cd and my sound works just fine in there. So i look at the logs see if i can find anything useful and find a 3 posts around the same time i rebooted that says "ubuntu pulseaudio[1604]: pid.c: Daemon already running."

I found something in another thread that, posted from another user, suggests un-installing pulseaudio and reinstalling it. So i did and still no audio but the sound control icon on the top bar is missing now.

Im trying to avoid reinstalling cause i just got everything setup on 10.10 the way i like it.

side note: for the most part, i know my way around linux, but im completly lost when it comes to sound issues.

---

### Post by LakatosI on 2010-10-21
This same problem confirmed on an ASUS K52JK laptop. Any suggestions?

---

### Post by kkady32 on 2010-11-12
%gnome-volume-control-applet

---

### Post by lidex on 2010-11-12
Try removing your pulse config files. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

Next provide more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sharonbose on 2011-04-08
> **lidex said:**
> Try removing your pulse config files. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Logout/in.**

Next provide more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Team ..I am also have the same issue 'Sound Card not detected any more'
more info is uploaded to the below site....
[http://www.alsa-project.org/db/?f=dee0aceb050c46682c0cd62dbc79000a8b809d8d](http://www.alsa-project.org/db/?f=dee0aceb050c46682c0cd62dbc79000a8b809d8d)

---

### Post by lidex on 2011-04-09
@sharonbose
What did you do?[-X
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by sharonbose on 2011-04-11
Thanks for  the reply...I did the same as you suggested but still no sound ...expecting your guidance to resolve  this issue

---

### Post by lidex on 2011-04-12
> **sharonbose said:**
> Thanks for  the reply...I did the same as you suggested but still no sound ...expecting your guidance to resolve  this issue

Can you run the alsa-info script again please?

---

### Post by sharonbose on 2011-04-12
Please find below the script o/p
 [http://www.alsa-project.org/db/?f=5bc773cf8a1b2ebc82ece42f67abb50b1997b61c](http://www.alsa-project.org/db/?f=5bc773cf8a1b2ebc82ece42f67abb50b1997b61c)

---

### Post by lidex on 2011-04-13
> **sharonbose said:**
> Please find below the script o/p
 [http://www.alsa-project.org/db/?f=5bc773cf8a1b2ebc82ece42f67abb50b1997b61c](http://www.alsa-project.org/db/?f=5bc773cf8a1b2ebc82ece42f67abb50b1997b61c)

It didn't take. Installed backports/alsa modules will interfere with that. Can you post this output please:
```
dpkg -l | grep "alsa"
```

---

### Post by sharonbose on 2011-04-15
dpkg -l | grep "alsa"
ii  alsa-base                             1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-utils                            1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                            4.69-0ubuntu2                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.30-2                                       GStreamer plugin for ALSA

---

### Post by lidex on 2011-04-17
@sharonbose
Try this:
```
sudo apt-get install --reinstall linux-image-2.6.35-22-generic linux-headers-2.6.35-22-generic && sudo dpkg-reconfigure linux-image-2.6.35-22-generic linux-headers-2.6.35-22-generic
```
Now reboot.

---

