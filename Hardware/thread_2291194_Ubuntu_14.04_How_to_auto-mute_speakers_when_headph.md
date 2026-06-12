---
title: "Ubuntu 14.04 How to auto-mute speakers when headphones plug in?"
date: 2015-08-18
forum: Hardware
---

### Post by Riemens on 2015-08-18
When I'm listening to some music, the speakers play the sound. But when I plug the headphones in (normal jack), the sound plays through both the speakers and the headphones.

How to auto-mute the speakers when I plug my headphones in my laptop?

Alsa mixer auto-mute doesn't work for me.

Edit: I looked for a solution many times, couldn't find it.

---

### Post by astralnysledz on 2015-08-19
I'm using Lubuntu 15.04 and it relies on PulseAudio, rather than ALSA. On my standard desktop PC plugging in headphones disables internal speakers. Maybe pavucontrol for PulseAudio would have the respective options?

Hope you will find your answer eventually :).

---

### Post by Riemens on 2015-08-20
I downloaded PulseAudio. But can find the option to mute the speakers when the headphones plug in.

Is there a command for it?

Thanks

---

### Post by Yellow Pasque on 2015-08-20
> How to auto-mute the speakers when I plug my headphones in my laptop?
It should be enabled by default. If it does not happen, then either it's disabled in alsamixer (which you have already eliminated as a possibility) or it's a bug. Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

