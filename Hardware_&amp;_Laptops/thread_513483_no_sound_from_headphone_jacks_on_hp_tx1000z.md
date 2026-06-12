---
title: "no sound from headphone jacks on hp tx1000z"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by guttersnipe on 2007-07-30
I finally got audio working on my new HP tx1000z laptop.  I edited /etc/modprobe.d/alsa-base and added
```
options snd-hda-intel model=3stack
```
...to the bottom of the file.

After that, I reboot or do a
```
#rmmod snd-hda-intel && modprobe snd-hda-intel
```
...and whala! I have sound out of the built-in speakers.  Even the microphone works.

The problem, however, is that I get absolutely nothing when I plug in my headphones into one of the two headphone jacks on the front of the laptop.

In alsamixer, there is a headphone "column" item, but pressing the up arrow does nothing.  I can mute and unmute it by pressing "m", but it still won't play to the jack.

Any ideas??

---

### Post by ugm6hr on 2007-07-31
Try unmuting and maximising all the alsamixer volume channels.

On my laptop (Acer) - the headphones are "Front" and internal speakers are "Surround"

---

### Post by sauronsmatrix on 2007-12-26
Check this out, solution has worked for everyone so far:
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

---

