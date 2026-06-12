---
title: "Internal mic makes noise hp pavilion dv9000"
date: 2010-06-07
forum: Hardware
---

### Post by wasabishot on 2010-06-07
Hello there!

I'm having a problem with my internal mic in my Hp Pavilion dv9730us.
It works , but with a distortion sound... really bad one... so people in the other end don't want me to speak thru it.
when my external mic is plugged sound is ok...

any idea what might cause the problem? and how can it be fixed??

thanks in advance.

---

### Post by wasabishot on 2010-06-07
OOps forgot...

using Ubuntu Lucid Lynx 10.04

---

### Post by lidex on 2010-06-09
Use gnome-alsamixer to check your levels and for mic boost, etc.
Level may just be too high.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by wasabishot on 2010-06-14
Hey!
I copy paste my reply from the other thread, as I opened this one for that problem. hope we can continue here.

so lidex- i did exactly what u said, but after reboot it just doesn't load any sound card. 

It's important I mention that since a while I don't use pulseaudio as i removed it according to this thread: 

[http://ubuntu-ky.ubuntuforums.org/sh....php?p=8284273]("http://ubuntu-ky.ubuntuforums.org/sh....php?p=8284273")

I also saw your message in the other thread I opened for this problem.

so maybe more details will help. I'm working only with alsamixer, and thanks to some new gnome-applets I have a volume control designed for alsa.

when I open gstreamer-properties I can choose in the input tab between Alsa or OSS.

when I choose Alsa I can control the amount of noise in the mic with the "Digital" Scroll in the mixer, but it never stops at all, only when down to zero, but then I can't hear my voice either.

When choosing OSS I can't control the amount of noise but it is not too noisy, but still noisy, so can't use the internal mic.

I should say that in both cases when using an external mic (jack) so I can't hear noise at all, only when choosing Alsa and "digital" gain up to max.

any other ideas?

---

