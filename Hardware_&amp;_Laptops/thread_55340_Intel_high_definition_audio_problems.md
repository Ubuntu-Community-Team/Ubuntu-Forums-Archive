---
title: "Intel high definition audio problems"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by liquid8 on 2005-08-08
I have managed to get my sound to work on my speakers with the snd_hda_intel module, but i get no output through my headphones at all. The speaker volume is controlled by the headphone control in alsamixer and all the rest seem to do nothing. Anybody else encountered this problem before?

---

### Post by oedipus on 2005-08-08
Yea, i have the a similiar problem.  I'm using ncmpc to play music, and the volume control there controls the master volume, but my headphone volume is the only one that controls anything.

---

### Post by BigMadWolf on 2005-09-08
[QUOTE=liquid8]I have managed to get my sound to work on my speakers with the snd_hda_intel module, but i get no output through my headphones at all. The speaker volume is controlled by the headphone control in alsamixer and all the rest seem to do nothing. Anybody else encountered this problem before?[/QUOTE]
 yeah, i have the same problem with my laptop asus a6va :(
there is sound in the speakers but no sound in the headphones :(

---

### Post by savale on 2005-09-08
This will do the job: model z71v!

/etc/modules:
...
snd-pcm-oss
snd-seq-oss
snd-mixer-oss
...

/etc/modprobe.d/sound:
options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

---

### Post by BigMadWolf on 2005-09-08
:(

i had already this kind of config files :(

/etc/modprobe.d/sound
```
options snd-hda-intel model=w810 position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

end the same thing in modules :(

and it doesn't work...
you really have sound in your headphones ?

maybe i dont have written the right thing in model? i have a realtek alc880 model on a laptop asus a6va

---

### Post by savale on 2005-09-08
[QUOTE=BigMadWolf]:(

i had already this kind of config files :(

/etc/modprobe.d/sound
```
options snd-hda-intel model=w810 position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

end the same thing in modules :(

and it doesn't work...
you really have sound in your headphones ?

maybe i dont have written the right thing in model? i have a realtek alc880 model on a laptop asus a6va[/QUOTE]


chenge model w810 to z71v as said above :P will do the job  :wink:

btw a little bit offtopic: did someone tested infrared/firewire/bluetooth on a6va? The webcam won;t work at all for a while I think

---

### Post by BigMadWolf on 2005-09-08
i changed to z71v and i rebooted but it's the same, sound on headphones still doesn't work :(

do you use realtek alc880 oss or intel HDA alsa ?
are some chanels muted ?

---

### Post by savale on 2005-09-08
[QUOTE=BigMadWolf]i changed to z71v and i rebooted but it's the same, sound on headphones still doesn't work :(

do you use realtek alc880 oss or intel HDA alsa ?
are some chanels muted ?[/QUOTE]
 no channels muted and I use HDA alsa drivers.

---

### Post by BigMadWolf on 2005-09-08
do you have an asus a6va like me ?

how have you maked your sound work?
i installed from realtek alsa driver 1.O.9b
and what about you ? did you installed alsalib and alsautils ?
had you made another change on your sound cfg?

thx!

---

### Post by savale on 2005-09-09
[QUOTE=BigMadWolf]do you have an asus a6va like me ?

how have you maked your sound work?
i installed from realtek alsa driver 1.O.9b
and what about you ? did you installed alsalib and alsautils ?
had you made another change on your sound cfg?

thx![/QUOTE]

I used the manual for installing hda-intel on the wiki site. And yes I own the asus a6va
With the config I posted above I have headphone output. Maybe take a look if you haven't mute your headphone channel: check out "alsamixer" or amixer

---

### Post by BigMadWolf on 2005-09-11
i installed alsa 1.0.10rc1 and now it works !
thx savale i had to change to z71v, but on 1.O.9b it didn't work

do you have 1.0.9b or 1.0.10rc1 ?

on 1.0.10rc1 i have to increase the sound level at every reboot, the front sound is muted by default.
do you have the same problem ?

---

### Post by savale on 2005-09-13
[QUOTE=BigMadWolf]i installed alsa 1.0.10rc1 and now it works !
thx savale i had to change to z71v, but on 1.O.9b it didn't work

do you have 1.0.9b or 1.0.10rc1 ?

on 1.0.10rc1 i have to increase the sound level at every reboot, the front sound is muted by default.
do you have the same problem ?[/QUOTE]
 Yes I have the same problem after reboot. Thought I used the 1.0.9b.... Maybe they will fix it in the new drivers.

---

### Post by kbuel on 2005-09-27
I have the same problem.. can't get sound through my headphones.
How do you install the 1.0.10rc1 drivers? Is there a ubuntu deb package?

Thanks a lot
K

---

### Post by BigMadWolf on 2005-09-27
no i think there isn't any deb package for ubuntu.
i'm a noob on linux, and compiling alsa drivers isn't very difficult.

1/ download alsa driver and unzip it, then :
```
./configure --with-oss=yes --with-cards=hda-intel
make
sudo make install
```

2/ download alsa library, unzip it, then :
```
./configure
make
sudo make install
```

3/ once you did that for library, do the same thing for oss-lib and utils

4/ Run ```
sudo alsaconf
``` and configure the sound card

5/ then reboot !

---

### Post by kbuel on 2005-09-27
Cool Thanks!

I'll try it as soon as I get home

---

### Post by kbuel on 2005-09-27
Well i installed version 1.0.10rc1 of all these packages:
alsa-base
alsa-oss
alsa-tools
alsa-tools-gui
alsa-utils
libasound2
linux-sound-base

and i did this:

/etc/modules:
...
snd-pcm-oss
snd-seq-oss
snd-mixer-oss
...

/etc/modprobe.d/sound:
options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

but i still can't get the headphones to work.  I have an asus z71v with HDA intel sound.

thanks for the help in advance!
K

---

