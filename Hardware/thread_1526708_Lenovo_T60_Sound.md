---
title: "Lenovo T60 Sound"
date: 2010-07-08
forum: Hardware
---

### Post by VanillaGorilla- on 2010-07-08
I have a Lenovo T60 with Ubuntu 10.04 installed. Someone else did the install for me.

I am not getting any sound output from the speakers or headphone jack. I am not to familiar with Ubuntu, but I have had some practice within school.

I've tried to Google for the answer but came up with nothing to straight forward when it came to an answer. The laptop uses the Intel HDA driver.

If you need anymore information let me know.

Thanks

---

### Post by mörgæs on 2010-07-08
Hi, welcome to the forum.

This might help you:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-07-09
Run alsamixer and check that levels are up and unmuted. Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
No help? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Matthes on 2010-08-12
> **lidex said:**
> Run alsamixer and check that levels are up and unmuted. Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
No help? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
I think I have the same problems as VanillaGorilla.
I made a new thread before: [http://ubuntuforums.org/showthread.php?t=1550797](http://ubuntuforums.org/showthread.php?t=1550797)

Here's my output :) :

 uname -a
Linux t60 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 dpkg -l | grep "alsa"
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                   1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                        14.3.0-1.1build1                                SoX alsa format I/O library
ii  xmms2-plugin-alsa                      0.7DrNo-4ubuntu1                                XMMS2 - ALSA output

 head -n 1 /proc/asound/card*/codec#* 
Codec: Analog Devices AD1981

---

