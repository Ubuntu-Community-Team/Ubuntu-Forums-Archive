---
title: "PulseAudio, Jaunty, XPS M1530 Volume Controls"
date: 2009-07-23
forum: Hardware
---

### Post by jdkchem on 2009-07-23
In alsa the volume controls on the laptop are tied to the output.  Having "switched" to PulseAudio the volume controls on the laptop are now tied to the input.  Now when I want to adjust the volume or mute instead of muting the speakers I am muting the microphone.


[Fixed] - More or less!  Updating to the newest pulseaudio from [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa) 0.9.15  fixes the problem.  It also appears to "fix" some Skype problems.  However, if you are using Skype do not open Banshee and start listening to tunes as you will lose audio output.  Also you'll only get mono, and do not use pulse as the device because the sound quality is horrible.

Unfixed - for whatever reason the controls are back to adjusting the input rather than the output.

---

### Post by mordecai83 on 2009-09-22
Hi

I experienced the same problem with the volume controls after installing PA 9.15 however i fixed it by going to system> Preferences> sound  and then selecting HDA Intel (Alsa Mixer) as device in "Default Mixer Track". Hope this works for you too.

With kind regards,
Mordecai

---

