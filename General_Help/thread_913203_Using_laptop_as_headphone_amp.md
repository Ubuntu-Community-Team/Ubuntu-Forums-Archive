---
title: "Using laptop as headphone amp"
date: 2008-09-07
forum: General Help
---

### Post by slapnuts on 2008-09-07
Hi

I am trying to use my laptop as a volume amp for my Xbox 360. Input and output are standard 3.5mm headphone jacks. I can record sound from Xbox fine with Sound Recorder and play it back fine. However I need some program that will pass through sound realtime. Also it would really help if I could somehow boost the volume (similar to the Normalize Audio option in gmplayer) 

thanx

---

### Post by decoherence on 2008-09-07
should be simple. set your system volume so that any built-in mics and external speakers are muted (you can use alsamixer for that) then use ```
aplay /dev/dsp
``` to play the dsp device (which will probably include your line in from the xbox)

---

### Post by slapnuts on 2008-09-07
> **decoherence said:**
> should be simple. set your system volume so that any built-in mics and external speakers are muted (you can use alsamixer for that) then use ```
aplay /dev/dsp
``` to play the dsp device (which will probably include your line in from the xbox)

Nah didn't work

:~# aplay -f cd /dev/dsp
Playing raw data '/dev/dsp' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
underrun!!! (at least 511.865 ms long)

---

### Post by -Zeus- on 2008-09-07
> **slapnuts said:**
> Nah didn't work

:~# aplay -f cd /dev/dsp
Playing raw data '/dev/dsp' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
underrun!!! (at least 511.865 ms long)

it's a microphone; why are you setting the input type to cd???

---

### Post by slapnuts on 2008-09-07
> **-Zeus- said:**
> it's a microphone; why are you setting the input type to cd???

Otherwise the default bitrate is way too low. I would imagine that I'd be losing a lot of quality if I did that

---

### Post by decoherence on 2008-09-08
> **slapnuts said:**
> Otherwise the default bitrate is way too low. I would imagine that I'd be losing a lot of quality if I did that

Well, I don't know much about aplay. Have you tried setting the bit rate manually (without also setting the format)?

Also, perhaps to get play through at a higher bitrate you need a real time kernel? That doesn't seem quite right though... the regular kernel should be able to handle simple play-through unless you're on pretty old hardware or your system is under a heavy load.

anyway, i'll let you know if i think of anything else. it's an interesting request so please keep us up to date if you figure something out.

---

