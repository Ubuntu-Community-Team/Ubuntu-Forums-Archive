---
title: "No sound with Logitech G930 wireless headset."
date: 2012-06-16
forum: Hardware
---

### Post by davedontmind on 2012-06-16
I've just installed Ubuntu 12.04 (64-bit, installed using Wubi, if that makes any difference) and everything so far seems to be working fine except for my Logitech G930 wireless headphones.

Despite seeing several messages in another thread saying these headphones work fine with 12.04, I get no sound out of them.

If I open Settings -> Sound, and connect the headphones I can see an entry for them in both the Output and Input tabs, as "Analog Output - Logitech G930 Headset" and "Microphone - Logitech G930 Headset" respectively.

The volume control on the headset controls the volume on the PC, but sound is only heard from the speakers, and never from the headset.

On the Output tab of the sound settings dialog, if I select the headset, then click the test sound button, the test sounds come out of the speakers.

On the Input tab, if I turn the input volume all the way up and talk loudly into the mic, I can hear myself through the headphones.

I have no idea how to troubleshoot this - can anyone help?

---

### Post by N0oki3 on 2012-06-16
```
sudo aptitude update && sudo aptitude install alsamixergui
```

then check in sound and video alsamixergui. 
I hope it helps

---

### Post by davedontmind on 2012-06-16
> **N0oki3 said:**
> ```
sudo aptitude update && sudo aptitude install alsamixergui
```

then check in sound and video alsamixergui. 
I hope it helps

Interesting.  aptitude doesn't see to be installed, but I used apt-get to install alsamixergui and ran that. It doesn't really have much in the way of options (just shows the title "Card: PulseAudio" and 2 volume sliders, Master and Capture).

However, without doing anything else, other than run it, when I went back to the Sound settings panel and selected the headphones, they now work.

They don't seem to switch to be the default audio device automatically when they're plugged in like they do in Windows (anyone know if they're supposed to?) which is slightly irritating, but when I manually select them as the output device it's all good.

I've no idea why installing & running alsamixergui would have had any effect though.

Thanks!

---

### Post by N0oki3 on 2012-06-16
> **davedontmind said:**
> I've no idea why installing & running alsamixergui would have had any effect though.
I've read once that somebody had auto-mute when he plugged in headphones...and he had to unmute them inside of alsamixergui.

And also mark thread as solved please

---

