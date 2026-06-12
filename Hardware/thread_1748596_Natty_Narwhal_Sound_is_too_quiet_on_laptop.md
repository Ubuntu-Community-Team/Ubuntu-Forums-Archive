---
title: "Natty Narwhal: Sound is too quiet on laptop"
date: 2011-05-03
forum: Hardware
---

### Post by Ace Slowman on 2011-05-03
Im running Natty Narwhal on my laptop (HDA Intel sound card I believe) and as of right now, I am getting very low volumes (it takes me turning it up to 100% to have it play at a decent level). Ive been reading around and Im getting some reccomendations about tinkering with ALSA's settings, but I really dont know how to start. I have also been using JACK, and I am getting even lower volumes there. One concern of mine is also sound quality; how can I assure that nothing will distort or lose any kind of clarity? Im a noob to all of this, any help would be appreciated.

---

### Post by jepperstone on 2011-05-03
My sound is also too quiet. I use Logitech USB headset by the way with pulseaudio.

Addendum: As I was typing this I looked at Sound Preferences and there is nothing about my Logitech headset. 

Under the Output tab, I am able to choose "Simultaneous output to Internal Audio Analog Stereo" and the sound is coming from my laptop speakers just fine. 
"RTP Multicast Sink" yields no discernable sound.
If I choose "Internal Audio Analog Stereo", then sound comes from my laptop only.

I wish to use my Logitech USB headset. Any ideas?

---

### Post by wariwahab on 2011-05-25
> **jepperstone said:**
> I wish to use my Logitech USB headset. Any ideas?

Same here. Adjusted all sorts of sliders in the sound preferences, and it's very soft. With my system freeze problem and this, a downgrade to 10.10 seems tempting.

---

### Post by silex89 on 2011-05-25
And if you use your headphones you get the same problem?, maybe is just a matter of a low power speaker (in general all the speakers in the laptops are around 5 W)

---

### Post by lidex on 2011-05-25
What is your amixer output:
```
amixer
```

---

