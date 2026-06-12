---
title: "Ubuntu 10.10 &amp; HP dv7-3165ef  Sound : Speakers and Headphone trouble"
date: 2011-01-03
forum: Hardware
---

### Post by sephiroth_slash on 2011-01-03
Hii guys,

I have an HP dv7-3165ef on ubuntu 10.10 64 bit, the problem was : when I plug the headphones, the sound plays on both headphone & speakers, after some searches on google I found a solution :

  1 - Go to a terminal and type : sudo gedit /etc/modprobe.d/alsa-base.conf
  2 - Copy and paste these 2 lines ( in the end of file would be good :p ) :
   
                        options snd-hda-intel model=thinkpad
                        options snd-hda-intel model=hp-dv5

  4 - Save & exit
  5 - Reboot

  
   Now the speakers should mute when you plug a headphone.

I tried "options snd-hda-intel model=hp-dv7" but I didn't work, and I noticed that the Subwoofer isn't working, but it's not a big deal :p

---

### Post by sephiroth_slash on 2011-05-04
I had the same problem on Ubuntu 11.04 amd64 , & this solution worked fine for me

---

### Post by lidex on 2011-05-04
Does this have beats audio? The standard fix is:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
For beats audio:
```
options snd-hda-intel model=ref
```
I would remove any other edits you made.

---

### Post by sephiroth_slash on 2012-03-18
this activates the beats audio, but still the problem of the headphones with the speakers

---

