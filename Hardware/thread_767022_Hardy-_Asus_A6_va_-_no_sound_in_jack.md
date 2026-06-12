---
title: "Hardy- Asus A6 va - no sound in jack"
date: 2008-04-25
forum: Hardware
---

### Post by r4w on 2008-04-25
Hi everyone.

I've upgraded my laptop to the new Hardy version and I can't get sound through the jack.

I know the common solution it's generally adding options snd-hda-intel model=z71v position_fix=1 to /etc/modprobe.d/alsa-base and that there are many threads about similar problems but I had successfully configured the previous version and for the more I've been trying this time I'm not getting any results.

Thanks in advance for your help,
r4w

---

### Post by arkangel on 2008-04-26
[PHP]gksudo  gedit /etc/modprobe.d/alsa-base
[/PHP]

and add these lines  at the end
[PHP]options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss[/PHP]

then restart the card

[PHP]sudo /etc/init.d/alsa-utils restart[/PHP]
try  alsasound  if you dont have alsa-utils    

open alsamixer
[PHP]alsamixer [/PHP]
arrows to move , go to Headphones , press "m" to  mute/unmute  arrows up/down to change the volume

---

### Post by r4w on 2008-04-27
Problem sorted out!
Thankyou:)

---

