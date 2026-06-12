---
title: "snd-hda-intel not working?"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by dragon_master_mokuba on 2007-11-18
Hi. I have a Toshiba L35-S2151. I just installed gutsy gibbon from the live CD for the 3rd time because i have been trying to get my headphones to play. i cant seem to figure out whats wrong. all the 'fixes' ive found are to mute the internal speakers when the headphones are plugged in. but it already does that without having to 'fix' anything. the internal speakers ARE muted when i plug the headphones in, but no sound plays from the headphones. and i have no option for headphones when i go into my volume settings. its driving me crazy >.< im half tempted to go back to using feisty because i COULD get the sound working thru the headphones. but that fix doesnt work on gutsy. can anybody help me?

---

### Post by sanone on 2007-11-18
Have you looked at some of the tips here [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) ?

It worked for my Acer Aspire 5315

---

### Post by dragon_master_mokuba on 2007-11-22
yeah i have. none of them worked >.< i just installed it again (i wanted to move it to a new partition lol) and now the headphones DO work, but the internal speakers dont. its wierd. im scared to install the updates because i like having my headphones working. any ideas how to get internal speakers working?

---

### Post by sanone on 2007-12-15
Sorry but these tips worked for me.
I assume you already tested the volume applet and System -> Preferences -> Sound.

Other then that I have no ideas.. goodluck!
San

---

### Post by spec456 on 2007-12-17
You can try this:

If you have an intel HDA sound card, then type in the terminal:

```

sudo gedit /etc/modprobe.d/alsa-base

```
Then at scroll down and at the end add:


```
options snd-hda-intel model=3stack
```

Then save and restart your computer and the sound should work. Let me know how it goes.

---

