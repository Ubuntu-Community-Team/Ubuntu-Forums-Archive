---
title: "Asus a6va, no sound trough headphones"
date: 2008-07-18
forum: Hardware
---

### Post by HandleWithCare on 2008-07-18
Hey, I tried watching a movie the other day on my asus a6va running hardy. As I was sitting in the train I used headphones. Bummer, no sound. I thought there must be an easy fix. But no. 

I found some solutions like turning on/off surround or adding aline like
snd-hda-intel model=z71v position_fix=1
to /etc/modprobe.d/alsa-base (as proposed [here]("http://www.burak-yueksel.de/2008/04/28/setting-up-ubuntu-804-on-asus-a6va/")) but none of them seems to work. I'm clueless at the moment. Anybody got an idea?

btw, the output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lambdA^ on 2008-11-27
hi, i'm running ubuntu 8.10 on my asus a6va and the problem you're describing was solved after i added the line
```
options snd-hda-intel model=z71v position_fix=1
```

everything else works out of box.

what about a dist upgrade? :)

---

### Post by HandleWithCare on 2009-01-18
Jut came across this thread again and I see in your reply that everything works out of the box for you in 8.10
I'm running 8.10 as well and got the headphones problem fixed. But I can't say everything works, definitely not out of the box. Like [Fn]+[F1] -> sleep; it will goto sleep, but it will never wake up (turn on but before I can unlock (it flashes for a second) It got back to sleep. And what about the media-keys. They worked in feisty, but since hardy they do nothing. And since I have a bisoncam integrated I will not be able to use my webcam.
I'm very curious whether these things workfor you

---

### Post by Campusanis on 2010-01-13
I've got an A6VA, am on Ubuntu 9.10 now and the webcam does work out of the box! Admittedly, it's not very good quality in darker places, but I'm still glad it works at all. So do the media keys, but I don't know how to configure them... The endless sleep thing is still annoying, though, but I can live with it...

---

### Post by bndevelop on 2013-01-12
solved it,


```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

adding ate the end of the file the line:

```
options snd-hda-intel model=z71v enable=1 index=0 position_fix=1
```

Don't forguet to use alsamixer to activate the sound after intalling the drivers.

:popcorn:

---

### Post by overdrank on 2013-01-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

