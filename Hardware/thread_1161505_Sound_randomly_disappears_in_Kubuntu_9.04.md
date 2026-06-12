---
title: "Sound randomly disappears in Kubuntu 9.04"
date: 2009-05-16
forum: Hardware
---

### Post by UrbenLegend on 2009-05-16
I have a HP Pavilion dv5t laptop with HDA Intel audio. Usually sound works fine at startup, but after a few minutes or hours it randomly stops working. Often I would leave my computer unattended for 15 minutes and come back to find that the sound no longer works and I would have to restart. I have a feeling that it has something to do with either leaving my computer unattended or running Pidgin with sound enabled. Pidgin's sounds play with a really annoying crackle (I heard this is due to an issue with the kernel?).

This problem is quite a nuisance as I have to stop whatever I am doing and restart my entire computer just to get sound to work again. I've tried killing PulseAudio and restarting it, but it didn't do anything.

What is the issue here and is there a way to solve/workaround it?

---

### Post by UrbenLegend on 2009-05-16
It just stopped right now when I changed videos in youtube. So its not a problem with pidgin or leaving my computer unattended as I was doing neither. I guess it just shuts off randomly.

---

### Post by alistair77 on 2009-05-17
Exactly the same problem on my Acer Aspire 3000

---

### Post by UrbenLegend on 2009-05-19
Bump. Anybody know how to fix this?

---

### Post by UrbenLegend on 2009-05-26
I've been googling about and found this link:

[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

The problem has been listed under the basic troubleshooting section. Guess we're gonna have to wait for an update. Meanwhile, it lists a way to restart ALSA and Pulseaudio to get sound working again. Here's the workaround:```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```I'll try this the next time it stops.

---

### Post by UrbenLegend on 2009-05-29
Good news is that the temporary fix works so I no longer have to restart my system when my sound fails.
Make sure to restart kmix or whatever volume control app you're using after running the commands.

EDIT: Actually, restarting ALSA is enough to fix the problem. Simply execute
```
sudo alsa force-reload
``` and sound will be restored.

---

