---
title: "[SOLVED] No &amp;quot;headphone jack sense&amp;quot;"
date: 2008-05-31
forum: Hardware
---

### Post by molotov00 on 2008-05-31
Spent several hours on this. Here's the problem:

I plug in headphones and the speakers on my Lenovo N200 continue to play.

I've tried the settings in Settings>Sound and Alsa Mixer.

Tried many forums and looked at bug reports. Looks like most people fixed the issue by checking a box for "Headphone Jack Sense". I don't see any such option in any of my sound settings.

I even checked /var/lib/alsa/asound.state and see entries for all inputs and outputs except this elusive "Headphone Jack Sense" switch. I also see that I can disable headphones through the driver, but not the speakers!

It looks like either I'm an idiot and can't find the right checkbox, or the GUI has changed (many of these "bug reports" go back years), or it's an alsa driver issue.

Please help! This is a real nuissance. 

I'll be glad to post any output that may be of use.

M

---

### Post by CazperII on 2008-05-31
You should try to add: 

options snd-hda-intel position_fix=1 model=lenovo

to /etc/modprobe.d/alsa-base

The position-fix=1 solved the problem you have with my N200. Remember to check the headphone option in the switches tab in the sound mixer, and unmute all the sliders.

---

### Post by silberj on 2008-05-31
I have this same problem on my Toshiba Satellite. Is there a similar fix for this?

---

### Post by molotov00 on 2008-05-31
> **CazperII said:**
> You should try to add: 

options snd-hda-intel position_fix=1 model=lenovo

to /etc/modprobe.d/alsa-base

The position-fix=1 solved the problem you have with my N200. Remember to check the headphone option in the switches tab in the sound mixer, and unmute all the sliders.

Thanks. That worked! I have to admit I don't know why it works... Previously I had the same line in my alsa-base file but had single_cmd=1 in place of position_fix=1. I hope this information can help someone else, so here's "N200 speakers not muted when headphones are plugged in" another time so Google will find it, haha.

Thanks again,
M

---

