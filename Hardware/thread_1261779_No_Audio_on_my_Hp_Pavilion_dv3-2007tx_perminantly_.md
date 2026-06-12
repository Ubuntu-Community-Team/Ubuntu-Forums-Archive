---
title: "No Audio on my Hp Pavilion dv3-2007tx perminantly muted"
date: 2009-09-09
forum: Hardware
---

### Post by teapottvroof on 2009-09-09
Firstly I'll sum up: I have No audio through speakers or headphones when running Ubuntu. I have touch controls above the keyboard, I can use them to make ubuntu increase volume, decrease volume, mute and unmute. When I am using windows the touch control for muting changes colour, orange for mute, blue for not mute. When I run Ubuntu it is always Orange.
Oh, and I'm a linux nube. :)

Ok so I bought me a new laptop, I was shocked to discover that no matter how powerful your system, windows can still clog it up... Programs crashed and internet dropped out.
I booted up Ubuntu and was pleasantly surprised to find my wireless internet worked fine :)  It seems to handle everything on my laptop fine, except for the audio. And we can't have no audio now can we. 

I am grateful to all who took time to read. I would appreciate any help or suggestions, thanks you very much.

---

### Post by dv3500ea on 2009-09-09
Try this:
press alt-f2 and type this:
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```This will open a text editor with a text file.
Scroll down to the bottom and add this line:
```
options snd-hda-intel model=hp-m4 enable_msi=1
```Then save and reboot.
That fixed the sound problems on my hp dv3.
I find I can't use the touch control but have to use the sound icon in the top menu bar on the right to change the sound. I have created a [thread]("http://ubuntuforums.org/showthread.php?t=1258788") here for problems with hp dv3 or similar laptops.

---

### Post by teapottvroof on 2009-09-10
Thank you I shall move to that thread.

---

