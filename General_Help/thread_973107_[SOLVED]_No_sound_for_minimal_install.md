---
title: "[SOLVED] No sound for minimal install"
date: 2008-11-06
forum: General Help
---

### Post by SteinbergerNate on 2008-11-06
Alright, I installed from a minimal install cd. I've gotten xfce working as well as some other programs. 

My main problem at the moment is that I have no audio. What do I need to install and configure to get audio working?

---

### Post by sisco311 on 2008-11-06
did you try *alsamixer* or any other volume control application to unmute the system volume?

---

### Post by SteinbergerNate on 2008-11-06
Well, mplayer was complaining about not being able to connect to pulse so I installed that. Here's the output of alsamixer in the terminal:
```

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused

```

---

### Post by sisco311 on 2008-11-06
try to kill pulseaudio and then try alsamixer again:
```
pkill pulseaudio
```

also post your kernel version and audio card type:
```
uname -r
lspci | grep -i audio
```

---

### Post by SteinbergerNate on 2008-11-06
Killed pulseaudio and still got the same output.

Kernel: 2.6.27-7-generic
Audio controller: 00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)

---

### Post by SteinbergerNate on 2008-11-06
I'm not too far into the setup of this install. I'm just going to do another clean install because I think I may have broken something.

---

### Post by mali2297 on 2008-11-06
Try
```

sudo alsamixer

```
Any luck?

---

### Post by SteinbergerNate on 2008-11-06
I'll let you know on the new installation. It's almost complete. Should I simply do a apt-get install alsa?

Keep in mind that I'm on a new install with nothing but the base system, xorg, xfce, fluxbox and firefox so it'll be a nice clean slate to work from.

---

### Post by sisco311 on 2008-11-06
you need the *alsa-base* package and *alsa-utils* (for alsamixer).

---

### Post by SteinbergerNate on 2008-11-06
Alright, alsamixer brings up just that in the terminal. I haven't tried to play any audio yet since I don't have any programs to actually do so yet.

I'll try to find a way to do that and see if I get sound.

---

### Post by SteinbergerNate on 2008-11-06
Ok, I'm trying to play an audio file in mplayer and I get a window that says this:

```
AO: [pulse] Failed to connect to server: Connection refused
```

What now?

The transport in mplayer is moving but there is no sound. If I play a video, the video plays but I have no sound.

---

### Post by sisco311 on 2008-11-06
try:
```
mplayer -ao alsa /path/to/file
```
or
```
mplayer -ao oss /path/to/file
```

---

### Post by SteinbergerNate on 2008-11-06
I found the correct slider to get sound in the mixer! I'm now getting mp3 output in mplayer. However, I'm still getting that error when I use the mplayer gui. Everything looks fine in the command line except that it's complaining about not having LIRC which is no big deal. 

What's the error message mean then if I'm getting sound? Can I get it to go away?

---

### Post by sisco311 on 2008-11-06
i don't have the gui installed, but if i right remember it's
an option in the properties to use alsa.

you also can add:
> ao=alsa
to the ~/.mplayer/config file.

---

### Post by SteinbergerNate on 2008-11-06
Thank you so much! This was the only problem I was having with my minimal install! You've been incredibly helpful and patient with me!

---

### Post by sisco311 on 2008-11-06
You're welcome!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

