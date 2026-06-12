---
title: "Sound won't play in games"
date: 2009-01-10
forum: Hardware
---

### Post by TekmonX on 2009-01-10
Hello Ubuntu Forums :), I have another question.

You see, When I open up a game like super tux, or Zsnes, the sound doesn't play. Also, in super tux, the sound is greyed out.

Am I missing some sort of thing for sound? The Sudo Lshw command says my sound device is 

" product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controlle"
And its from intel.

I've heard that sound not playing in games are common. So please bear with me,

Thanks in advance,
Tekmon Xonic

---

### Post by paziek on 2009-01-10
Do you have required sound drivers?
For example when I tried to play AmericasArmy on linux, I had to install OpenAL in order to get sound.
When you start those games from console, does it say something?

---

### Post by TekmonX on 2009-01-10
> **paziek said:**
> Do you have required sound drivers?
For example when I tried to play AmericasArmy on linux, I had to install OpenAL in order to get sound.
When you start those games from console, does it say something?

That's what I'm wondering, but the games usually don't say anything.

And what's OpenAL? Could that possibly help.

---

### Post by paziek on 2009-01-10
Well, AmericasArmy did told me, that it needs OpenAL for sound, so sometimes games do say some helpfull stuff :)

OpenAL is.. like OpenGL, but for sound :)
You can install it via
```
sudo apt-get install libopenal-dev
```
and don't worry - it won't break anything - you can have OpenAL, Alsa, PulseAudio or whatever at the same time. Or at least it shouldnt.

---

### Post by TekmonX on 2009-01-10
Alright, that didn't work. :)

---

### Post by paziek on 2009-01-10
Hmm, do you have sound in - for example - music player? Flash or whatever else?

---

### Post by TekmonX on 2009-01-10
> **paziek said:**
> Hmm, do you have sound in - for example - music player? Flash or whatever else?

Well, I have sound in kaffine, flash, tux racer, World of padman, termlous.

But I don't have sound in Super Tux, Warzone 2100, and Zsnes.

---

### Post by paziek on 2009-01-10
Huh, perhaps try installing all kinds of "drivers" ;P
alsa, oss, pulseaudio, jack, arts, esound
look for them in synaptic

Or wait for some1 with more knowledge on that issue.

---

### Post by TekmonX on 2009-01-10
> **paziek said:**
> Huh, perhaps try installing all kinds of "drivers" ;P
alsa, oss, pulseaudio, jack, arts, esound
look for them in synaptic

Or wait for some1 with more knowledge on that issue.

Okay, I'll install what I can find.

Thanks :)

---

### Post by markbuntu on 2009-01-10
I think those are SDL apps. In that case you need

libsdl1.2debian-pulseaudio

---

