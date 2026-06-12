---
title: "Laptop CD volume very low"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by gorb on 2007-06-06
Hey ppl,

I have a Fujitsu-Siemens M1451G Amilo laptop, and so far have had Fiesty run flawlessly on it for a couple of weeks now. Very impressive!

I do seem to have one tiny problem though, and it seems so tiny that I can't find any reference to it using google: when playing a cd through grip or cdtool, the volume is so low that I can barely hear it, even though I turn every single volume control up to 100%.

However, using Sound Juicer, or something like
$ gst-launch-0.10 -v playbin cdda://1
gives normal level volume playback. I have to turn the volume down to 80% not to go deaf. The same goes for any other digital audio media. Playback volume is normal. Mp3s, wmas, everything works.

The only thing that seems to be affected is direct cd playback.

Info:
lspci says:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
  Definition Audio Controller (rev 04) 0

Checks:
* nothing in my ears (since I can hear the mp3s)
* amixer says all controls are high enough (since I can hear the mp3s)

Problems so far:
* there is *no* CD entry, neither in alsamixer nor in gnome's mixer app.
(My guess would be that the problem lies somewhere around here... but where?)

What I have tried:
* I have followed the instructions listed in
  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
  and have succesfully installed alsa 1.0.14rc4.
  No improvement though.
* I have added the line "options snd-hda-intel model=auto" to /etc/modprobe.d/alsa-base.
  No improvement.

Does anyone have the same problem?

PS: Before anyone asks, the reason why I want cdtool/grip to work, and why I do not want to use Sound Juicer, is that any app which (like SJ) uses cdda access causes the drive to spin up, which can become irritatingly loud. Using cdtool or grip, the *drive* plays the cd back, directly to the sound card/device, and therefore only spins up as fast as it needs to, which is not much - ie. it is not audible at all. At least, that is my understanding...

---

