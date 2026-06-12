---
title: "Acer Aspire 1830-3721 Headphones"
date: 2010-09-14
forum: Hardware
---

### Post by cfbmoo1 on 2010-09-14
I've an Acer Aspire 1830T-3721 and for the most part I've gotten everything to work with Ubuntu 10.04. The only real problem I'm having at the moment is the headphone jack. Sound appears to work from the internal laptop speakers but when I plug in the ear buds there is no sound.


[LIST]
[*]Two days ago I had Windows 7 on this machine and sound worked fine with and without ear buds.
[*]Tested ear buds today on another PC and they worked fine.
[*]aplay -l listed the following devicdes
[/LIST]
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[LIST]
[*]head -n 1 /proc/asound/card*/codec#*
[/LIST]
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
```
[LIST]
[*]cat /proc/asound/version
[/LIST]
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```I'm a bit confused as to what I need to do to resolve this problem. Some posts have said to upgrade to the latest version of ALSA but then it won't register properly with the regular package system since your putting stuff in through a back door basically. I know the sound card is there, working, but it just doesn't handle the switch over to ear buds.

Any help would be appreciated.

---

### Post by cfbmoo1 on 2010-09-14
Got brave even though I saw this listed for different hardware I figured I'd give it a shot.

[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

After downloading the script from the bottom of the post and running the script with the various options listed from the short version install instructions my sound is now working for my hardware.

---

### Post by schmickey on 2010-09-19
Worked for me too.  The guy that wrote that script deserves a medal!

---

### Post by lidex on 2010-09-19
> **schmickey said:**
> Worked for me too.  The guy that wrote that script deserves a medal!

That would be *soundcheck*
I refer people to that script daily [it's in my sig]. He does indeed deserve accolades.

---

### Post by cfbmoo1 on 2010-09-20
I lost my sound card over the weekend. I think it was a kernel update that nailed it. Still I ran steps 4-7 and it's back up and running again.

---

### Post by scarleo on 2010-10-09
For me I got the headphones working just by installing linux-backports-modules-alsa-lucid-generic from package manager. Guess I don't have to redo t then if there is an update.

---

