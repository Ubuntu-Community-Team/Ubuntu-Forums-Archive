---
title: "No sound 8.10"
date: 2008-11-29
forum: Hardware
---

### Post by ralph.p on 2008-11-29
Hey, I spend 2 days on google trying to find a solution to my no-sound-problem. I tried many things but I still havent any sound on my fresh installed 8.10. 

Image of my sound-configuration:
[http://i38.tinypic.com/xfanmu.jpg](http://i38.tinypic.com/xfanmu.jpg)

When I choose HDA ATI HDMI (ALSA) it tests but i cant hear anything. When I choose something different I get an error.

I installed alsermixgui but when I click on it nothing happens..

I read and tried most of the possible (complex) solutions te be find in the internet.

Ty, 
ralph

---

### Post by ralph.p on 2008-11-29
I have a "HD audio" sound card and have some troubles updating its right drivers..

E: Couldn't find package linux-backports-modules-generic

---

### Post by akshay.sulakhe on 2008-11-29
try plugging ur speaker wire in the front port..i did the same....but if u have a sound card that is very advanced then cant help...

---

### Post by ralph.p on 2008-11-29
didn't help. i'm getting desperate ...

---

### Post by ralph.p on 2008-11-30
when I did 
```
sudo killall pulseaudio

sudo alsa force-reload
```

I still have no sound but now I can open alsamixergui

[IMG]http://i36.tinypic.com/34tai2u.jpg[/IMG]

---

### Post by sgeoxd on 2009-04-10
If having the same issue, what are you physically outputting as?  HDMI to an external device?  If you haven't tried this:
```
sudo nano ~/.asoundrc
```

Add:
```
pcm.!default spdif
```

Save, close, and run this:
```
speaker-test -c 2
```

Hopefully something comes out.  Be sure to delete the file when done to avoid other problems:
```
sudo rm ~/.asoundrc
```

You also want to make sure IEC958, "Master", and PCM are unmuted:
```
alsamixer
```

This has also worked for some:
```
/usr/bin/iecset audio on
```

More info from [here.]("http://xbmc.org/forum/showthread.php?t=35901")

---

