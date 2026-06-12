---
title: "No sound on ASUS N82J Laptop under Lucid Lynx"
date: 2011-01-02
forum: Hardware
---

### Post by zvib on 2011-01-02
Hi there,
I have no sound on my laptop under Ubuntu Lucid Lynx. I have looked on this forum and others for a solution but nothing has worked until now.

I'll copy/paste some commands which might help someone to see the problem.

Cheers

uname -a
```
Linux ubuntu 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
```aplay -l
```
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC269-VB Analog [ALC269-VB Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC269-VB Digital [ALC269-VB Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 3 : INTEL HDMI 0 [INTEL HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 7 : INTEL HDMI 1 [INTEL HDMI 1]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```dpkg -l | grep "alsa"
```
ii  alsa-base                                                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                                           1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                                         0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  alsaplayer-alsa                                                      0.99.80-5                                       PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                                                    0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-daemon                                                    0.99.80-5                                       PCM player designed for ALSA (non-interactiv
ii  alsaplayer-gtk                                                       0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                                                       0.99.80-5                                       PCM player designed for ALSA (OSS output mod
ii  bluez-alsa                                                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                                   0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-27-generic                       2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic                           2.6.32.27.29                                    Backported drivers for alsa-driver snapshot.

```dpkg -l | grep "alsa"
```
ii  alsa-base                                                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                                           1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                                         0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  alsaplayer-alsa                                                      0.99.80-5                                       PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                                                    0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-daemon                                                    0.99.80-5                                       PCM player designed for ALSA (non-interactiv
ii  alsaplayer-gtk                                                       0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                                                       0.99.80-5                                       PCM player designed for ALSA (OSS output mod
ii  bluez-alsa                                                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                                   0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-27-generic                       2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic                           2.6.32.27.29                                    Backported drivers for alsa-driver snapshot.

```Thanks if you read this and try to help me...

PS: You could also find the alsa-info output at [http://www.alsa-project.org/db/?f=a671e855e01586e6a8c769a095c54ac002a74a42](http://www.alsa-project.org/db/?f=a671e855e01586e6a8c769a095c54ac002a74a42)

---

### Post by VespaModaiolo on 2011-02-12
I just resolved the same issue with my brand new Asus N82J w/ a fresh Lucid install...

Go to sound preferances -> select the hardware tab -> go to the Drop Down Menu and Select *Analog Surround 4.0 Output + Analog Stereo Input*.

Problem Solved (at least for me), Good Luck!

---

### Post by etiennenoel on 2011-03-01
Hi, I've got an Asus N82J and I have a similar problem. When I plug a headphone in the jack, I get sound in my headphones. However, nothing in my speakers. I did the following things :

I did this command :

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
Now the upload link is:
[http://www.alsa-project.org/db/?f=f19324ba1698e62530bf18604db63e568d42b11c](http://www.alsa-project.org/db/?f=f19324ba1698e62530bf18604db63e568d42b11c)

Also, I did the following : 
 	Code:
 	sudo add-apt-repository ppa:ubuntu-audio-dev/ppa sudo apt-get update 
Now install:
 	Code:
 	sudo apt-get install linux-alsa-driver-modules-$(uname -r) 
**Reboot**
Check your levels in alsamixer.


[FONT=monospace]and the levels were fine.
[/FONT]
Now, after that I got more choices in the output tab. I tried to put it to Select *Analog Surround 4.0 Output + Analog Stereo Input* without success. I even rebooted but nothing changed.

Now I was wondering that maybe I'm missing a step and someone could help me.

Thanks in advance !

Etienne NOEL

---

