---
title: "Sound loops"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Taleman on 2007-10-31
I'm using Ubuntu Gutsy with a HDA Intel sound card using Realtek ALC861. At first I had no sound so i used the hack

kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto


After I did this the sound started working but it would just loop the audio. So for example when i login the first 2 seconds of the login sound continuously repeats. any other sound file a play also loops the same way over the already looping sound. Also alsamixer seems to have no effect on it. wheni I try to adjust the volume or mute it, nothing happens the sound just continues to play at the same volume.

---

### Post by Taleman on 2007-11-01
Is there at least some way to undo this?

---

### Post by pastelero on 2007-11-01
I'm having a similar problem. Sound starts OK, but within some random time it stucks in a loop forever. I've tried using sound through ESD, OSS , ALSA and no results. I haven't found anything wrong in the error logs when this happens, so I don't know where to look the problem.

I've just upgraded to Gutsy. With Feisty I never had that problem. I have a Toshiba Satellite L25-S1216.

---

