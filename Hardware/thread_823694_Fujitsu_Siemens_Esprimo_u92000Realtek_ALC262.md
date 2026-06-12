---
title: "Fujitsu Siemens Esprimo u92000/Realtek ALC262"
date: 2008-06-09
forum: Hardware
---

### Post by Teuchert on 2008-06-09
Hi,

I just bought an Fujitsu Siemens Esprimo mobile u9200, designed for Vista and installed Ubuntu 8.04 LTS. So far everything works fine but I have trouble with the audio. When I plug in headphones it won't use them, instead it continues using the inbuildt speakers. There's also a quite heavy constant background noise when I don't mute the speakers. I also guess the plugged in microphone won't work (haven't had a chance to test it yet). The sound chip should be a Realtek ALC262

Does anyone know how I could get that fixed?

Cheers

---

### Post by jku on 2008-07-09
Hello

I own same machine as you and have been suffering the same problem. I did a little browsing in the web and found a solution for the problem. Link below should redirect you to website where you can find instructions. First solution, building alsa modules myself, worked for me. After resetting alsa-utils, new checkbox appeared to kmix. Now I can choose between headphones, speakers or both at the same time.

And here is the link
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/]("http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/")

---

### Post by patrickfromspain on 2008-07-11
Have a fix!

What I've done:

```

sudo apt-get install m-a
sudo m-a prepare
sudo m-a a-i alsa

```

Then, in a terminal gksudo gedit /etc/modprobe.d/alsa-base and, at the end, add the following: options snd-hda-intel model=sony-assamd

Now I get the sound right: I get sound from the speakers and these mute when I plug-in the headphones. As for the microphone, it sort of works, but it's very noisy, not usable.

Hope it helps!

EDIT: the headphones stuff also works by using model=benq-t31

EDIT2: after some more testing, I've found that the models that work are hippo, benq-t31 and sony-assamd.

---

### Post by bobishh on 2008-08-08
I just added "options snd_hda_intel model=hippo", and commented all other strings that begins with "options" that were listed in alsa-base, and reloaded alsa. So it seems that using module-assistant is not required.

---

### Post by wersdaluv on 2008-09-06
Perfect! :D

---

### Post by wersdaluv on 2008-09-07
Awww. Apparently, the microphone isn't working :( How do we fix this?

---

### Post by markwasheim on 2009-03-21
Hej guys. Threads a bit stale... but:

I've got the same machine, Ubuntu 8.10 have tried the alsa drivers from 1.17 to 1.19 (the latter compiled by hand) ...

In any case, even though the drivers work just fine, the front speakers are really low... other outputs, muting, recording (also with the webcam) all works, just the speakers seem way low.

It seems that the backport drivers are just fine and the correct setting in /etc/modprobe.d/alsa-base

options snd_hda_intel model=basic 

(hippo, one of the sony and one of the benq settings also work but are incorrect what some pinouts are concerned).

Any one have the same experience with the volume???

greets,
Mark

---

### Post by michopop on 2009-08-11
Before few months I got U9200 and decided to migrate from XP to Ubuntu. Now I am thinking about migrating back to XP because too many problems appeared. One of them is that I can't use the microphone device. Does somebody have any idea how to repair it???

---

