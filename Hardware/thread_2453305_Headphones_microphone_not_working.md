---
title: "Headphones microphone not working"
date: 2020-11-07
forum: Hardware
---

### Post by altruisticvariation on 2020-11-07
Whenever I plug my headphones (I have tried many headphones) into my laptop's combined input/output audio jack, sound is working but the microphone is not recognized in pavucontrol. I can only see the laptop's internal microphone. 

I have read many different questions on the forums and in most of them, answers suggest to edit */etc/modprobe.d/alsa-base.conf*. I have tried adding the following line:

```
options snd_hda_intel model=<model>
```

with different options for *<model>* found here: [https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html](https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html). Because I have an asus laptop with an alc255 card I tried models which had "asus" or "alc255" in the name. With some models, after a reboot, when I connected my headphones, a prompt appeared that asked me to select between headphones, headset and microphone, so that was an improvement. However the microphone still didn't work. 

What am I doing wrong? I need to have my headphones mic fixed because built-in microphone is noisy. I don't want to go back to Windows because of this.

---

### Post by CelticWarrior on 2020-11-07
Welcome.

Do all the headphones you tried also work with phones/tablets? If so, they should work with your laptop.
If they have separated jacks then obviously they won't work without an adapter.

---

### Post by altruisticvariation on 2020-11-07
> **CelticWarrior said:**
> Welcome.

Do all the headphones you tried also work with phones/tablets? If so, they should work with your laptop.
If they have separated jacks then obviously they won't work without an adapter.

The issue is with the microphone. They work on Windows in the same machine.

---

