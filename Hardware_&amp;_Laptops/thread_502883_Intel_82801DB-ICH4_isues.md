---
title: "Intel 82801DB-ICH4 isues"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by damotor on 2007-07-17
Hello.
I have an amilo m 1425 laptop wich has a intel I82801DBICH4 sound card. When  I'm working on gnome or fluxbox, several sounds can be played at the same time, but when I'm using gnome and I start fluxbox through the dgmflexiserver --xnest t won't play any sound in fluxbox if there's any application playing a sound in gnome. The error I get there is:
```
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
```
The other isue is that my laptop has two microphones and despite both appearing in the preferences none of them seem to work in ubuntu.
Here is my .asoundrc:
```
pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}

bindings {
0 0
1 1
}
}

pcm.dsp0 {
type plug
slave.pcm "dmixer"
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.default {
type plug
slave.pcm "dmixer"
}

ctl.mixer0 {
type hw
card 0
}

pcm.emu10k1 {
type hw
card 0
}

ctl.emu10k1 {
type hw
card 0
}
```

Regards.

---

