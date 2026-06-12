---
title: "MSI Megabook Gx600: Internal speakers dont shut up when pluggin in headphones"
date: 2008-08-21
forum: Hardware
---

### Post by Wauzl on 2008-08-21
Hello Forum,

I'm using a MSI Mesgabook Gx600 and the problem is, that I want to hear the sound only EITHER from the internal speakers OR from my headphones, but when I plug them into the headphones-jack, my internal speakers go on playing sounds.

The notebook has a hda-intel sound card with an ALC888 codec.

I have the latest alsa-base, drivers and utils running.
I added to my /etc/modprobe.d/alsa-base the following line:
```
options snd-hda-intel model=auto
```
and the same without "options" to /etc/modules
I tried more configurations, I tried targa-dig and targa-2chan-dig, too.
I also tried using some other mixers bzw. soundservers like PulseAudio, ESD and OSS.

I hope that anyone has some idea to fix this problem...

grüße und so

Wauzl

[EDIT] Im coming from figuring out, that I can control the volume in the Mixers, but it seems to be like that, that all rulers are mutiplied and set the sound level for the outputs, so when I turn the ruler for headphones down, the sound with is lower on the internal speakers AND the headphones. Same for the "front" and "PCM" -rulers. [/EDIT]

---

### Post by levidos on 2008-12-01
yeah, i have the same problem with my MSI EX600X-251EU notebook, intel high definition audio with alc888 codec on ubuntu 8.10 x86. did you figure how to fix the problem?

[EDIT]
this headphone problem is fixed by adding the **options snd-hda-intel model=targa-2ch-dig** line to the end of **/etc/modprobe.d/alsa-base** .
unfortunately after plugging in the front, rear and lfe+center jacks of my speakers into the notebook, i don't know how to tell the mixer to use them and send 5.1 sound.
[/EDIT]

---

### Post by Wauzl on 2008-12-02
Thanks levidos,

I already stopped searching for a solution. I actually did try lots of models but not this one..

It works fine after I changed the channel I can control with my keyboard to "Master" (it was PCM-2 and I could only mute or full-sound it).

Just one little problem rests: when I now mute the sound with the keyboard (Fn+F9 on my Megabook) and then un-mute it the sound comes from the internal speakers AND the external. It works fine when I replug the jack..

[EDIT] Dunno really why it firstly didnt work, now, I changed the channel I can control with my keyboard to PCM, now everythings fine.

PS: I don't have a 5.1-soundcard, so I cannot help you..
But I found [this]("http://ubuntuforums.org/showthread.php?t=871370"): maybe you can try ```
3stack-6ch
```
For this guy this 2 options worked, he's got the same codec.. So good luck![\EDIT]

---

### Post by levidos on 2008-12-14
neah, unfortunately it's not working as it should. in volume control there are "Surround", "Center" and "LFE" sliders, but if i plug a headphone in the purple or blue holes, i can;t hear anything. I also have to *UN*check the headphone switch to mute the internal speakers of the notebook.

mfG,
Levi

---

### Post by levidos on 2008-12-27
my experience is that targa-2ch-dig is working better with this MSI EX-600X notebook.

---

