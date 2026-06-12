---
title: "internal microphone in Vaio VGN-SZ450N doesn't work in Hardy Heron"
date: 2008-06-10
forum: Hardware
---

### Post by lasheimok on 2008-06-10
Hi all,

this Vaio VGN-SZ450N has Hardy Heron installed, and mostly works fine, but the internal microphone doesn't work.

I already added

options snd-hda-intel model=vaio
options snd-hda-intel model=3stack

to /etc/modprobe.d/alsa-base, as suggested in the forums, but it doesn't seem to make a difference.

I also tried to
sudo apt-get install linux-backports-modules-generic

but it replies "E: Couldn't find package linux-backports-modules-generic" even when "hardy-backports" is ticked in Software-Sources.

ALSA Mixer shows Card: HDA Intel, Chip SigmaTel STAC9872AK.

Master, PCM, Capture and Digital is shown and can be adjusted, but Mic Jack and Internal Mic can't be adjusted.

Any idea?

Thanx in advance! :)


Gratefully,
 Lasheimok

---

### Post by nlz on 2008-06-10
did you already tick the internal mic or mic jack?

You can do this if you open volume control, preferences and then tick the Jack and Internal, then you can select a tab with options or switches, and select the internal there. it worked for my vaio vgn fz31m.

---

### Post by Nepherte on 2008-06-10
> but it replies "E: Couldn't find package linux-backports-modules-generic" even when "hardy-backports" is ticked in Software-Sources.
It should be:
```
linux-backports-modules-hardy
```

As far as I know, all Sony laptops use the vaio model option.

---

### Post by lasheimok on 2008-06-11
Hi nlz, hi Nepherte,

I tried both of your suggestions and it works now.

Thank you so much! :)

Gratefully,
 Lasheimok

---

