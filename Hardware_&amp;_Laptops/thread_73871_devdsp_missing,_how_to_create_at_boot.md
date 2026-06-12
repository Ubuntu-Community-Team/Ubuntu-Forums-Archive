---
title: "/dev/dsp missing, how to create at boot?"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by uber_geek on 2005-10-10
I have to create my sound card every time I boot using 

[FONT="Courier New"]sudo mknod /dev/dsp c 14 3 && sudo chmod 777 /dev/dsp[/FONT], 

here is my /etc/modprobe.d/alsa-base 

[FONT="Courier New"# This sets up the ALSA and OSS portion
alias char-major-116 snd
alias char-major-14 soundcore

# Replace "driver" with the driver for you soundcard
alias snd-card-0 emu10k1
options snd_emu10k1 index=0
alias sound-slot-0 snd-card-0
]# Configure the OSS emulation layer
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/dsp snd-pcm-oss
alias /dev/mixer snd-mixer-oss
alias /dev/midi snd-seq-oss

# If you have more than 1 card, set this number to the correct value
options snd cards_limit=1
options snd-pcm-oss nonblock_open=1 [/FONT]

how do I create it at boot? it is really anoying to have to create it everything I want to use a OSS application such as skype.

any help grateful
chris

---

### Post by mlomker on 2005-10-10
> mknod /dev/dsp c 14 3 && sudo chmod 777 /dev/dsp

That would be frustrating.  You can add that line toward the end of /etc/init.d/bootmisc.sh

---

