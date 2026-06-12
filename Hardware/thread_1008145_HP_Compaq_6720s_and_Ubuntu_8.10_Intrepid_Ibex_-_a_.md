---
title: "HP Compaq 6720s and Ubuntu 8.10 Intrepid Ibex - a (hopefully) complete guide..."
date: 2008-12-11
forum: Hardware
---

### Post by slayer^_^ on 2008-12-11
HP Compaq 6720s and Ubuntu 8.10 Intrepid Ibex - a (hopefully) complete guide...


This the follow-up of the three-version old walkthrough to get this laptop working very well with Ubuntu...

Well, what to say... everything works very well, finally, with Ubuntu 8.10 Intrepid Ibex, except for the usual two or three things... however I am waiting for your suggestions!!!



**1) Getting wireless device to work**

Actually, my wireless work very well with the proprietary STA driver, but doesn't work at all using the b43 drivers. Instead of stucking with ndiswrapper once more, I am using this STA driver and I am fine... and I didn't change network-manager with Wicd too...

**2) Correctly configuring Skype**

Skype is one of the most diffused voip applications over the net, thus is very important to be able to use it under Linux.

_- SKYPE --> OPTIONS --> AUDIO DEVICES_
The settings should be like this:

HDA Intel (hw;Intel,0) / pulse / pulse

You can allow skype to set the levels of the mixer.

_Now try to use skype... if it works you can finish the procedure of configuration here, if it doesn't go forward with the instructions below:_

_- VOLUME CONTROL SETTINGS_
Double click on the volume control icon up in the panel; be sure that device is setted to "HDA Intel (Alsa Mixer)"; now click on "preferences" down in the window; be sure every box is selected, then close the window; these are the correct settings:

Reproduction : the first two to the maximum, the third one in the middle, the last one to the minimum or disabled
Recording: to the maximum, the microphone should be disabled by default
Switches : the microphone one should be enabled.

_- SYSTEM --> PREFERENCES --> AUDIO_
The settings in the first window should be like this:

Automatically identified / Automatically identified / Automatically identified / ALSA / HDA Intel (ALSA Mixer)


It should work like this, please note that i translated the infos above from an italian version of ubuntu (not so much time now...) so many terms may be different. I hope it's not too hard to find your way, in case let me know and i'll guide you asap.


**3) 3D Desktop Effects should work - Intel GM965**

This is a die-hard bug... still not fixed for 3D applications, however 3d desktop effects now work.
If you want to know more, take a look here...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834)

---

### Post by map84 on 2009-02-17
Owners of a HP Compaq 6720s running on Ubuntu 8.10 forgot about the following problem:

[http://ubuntuforums.org/showthread.php?t=1011914&highlight=hp+compaq+thermal](http://ubuntuforums.org/showthread.php?t=1011914&highlight=hp+compaq+thermal)

---

