---
title: "Another AC97 Audio Thread - Intel"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by PantherX on 2006-10-13
Hey all.  Went through all the forum posts on this topic and can't seem to figure it out for myself.  The computer itself is a t41p thinkpad.

lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

I even went into the mixer and tried multiple configurations in muting things and unmuting them and no dice.

From what I've been reading, everything should work all nice and happy like, but I still have no sound.

Any suggestions?

---

### Post by PantherX on 2006-10-19
Still trying to find a hack for this as it is a known issue (apparently), any help would be awesome.

---

### Post by Sef on 2006-10-19
This is how I solved my problem:

Applications > Accessories > Terminal

sudo gedit /etc/modprobe.d/alsa-base

you will see this:

```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```


Change the last two lines to this:

```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
# options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0 
```

Add a comment mark (#) in the penultimate line and change the 2 in the last line to zero (0).

---

### Post by PantherX on 2006-10-20
Yeah I had done that a few weeks ago with no success.

I did get it fixed yesterday.  It involved going into xorg.conf and commenting out anything to do with wacom tablets, restarting X and then running alsamixer again... and then storing to alsactl.

At least now I can listen to music... now if I can only find a good mp3 player that plays ogg.

---

### Post by Pablasso on 2006-10-31
Amarok and Xmms are just excelent and both play OGG's

---

### Post by linbie on 2006-10-31
> **PantherX said:**
> Yeah I had done that a few weeks ago with no success.

I did get it fixed yesterday.  It involved going into xorg.conf and commenting out anything to do with wacom tablets, restarting X and then running alsamixer again... and then storing to alsactl.

At least now I can listen to music... now if I can only find a good mp3 player that plays ogg.

Hi PantherX,

Would you mine sharing with me on how you get yours to be working? Seems like my sound card is somehow similar to yours.

lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

jacky@qin-jacky:~$ lsmod | grep snd
snd_intel8x0           33692  0
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

I'm using Ubuntu 6.06 LTS.

---

