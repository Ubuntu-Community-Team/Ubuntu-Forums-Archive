---
title: "internal mic on acer aspire 4736g"
date: 2010-09-07
forum: Hardware
---

### Post by alxgomz on 2010-09-07
Hello I have an acer Aspire 4736g bought in Thailand. It works great but i have some issues with the sound card. If analog output sound works ok, I can't get the internal microphone to work. 

I am running ubuntu 10.04 with kernel 2.6.32-24-generic i686
Alsa sees 2 mic:
input1: front mic (which i suspect to be the internal mic)
input2: mic (which the microphone i plug in the jack and works)

I have tried several options of the snd-hda-intel module to no avail (acer-aspire-4930g)
Here is what I can find in procfs:
cat /proc/asound/pcm 
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
00-03: NVIDIA HDMI : NVIDIA HDMI : playback 1

The NVIDIA HDMI audio output do not work either.
Does anyone has a clue or knows how to get it to work?

---

### Post by alxgomz on 2010-12-18
In fact I though it was not working at all during months. Everytime I
was trying to record anything I just got loud noise. But today I tried
speaking louder while recording and realised I could ear my voice
hidden behind the noise! Great news: the hardware part worked!
Going further in my test, I found that using plughw:0,0 as a device
for arecord make the noise diappear and gives me a very clean
recording (where hw:0,0 still gives a lot of noise)!
Unfortunately, the problem remains as most of my apps don't care about
plughw or hw, and only know about pulseaudio.

Does anybody knows how I could workaround this?

---

