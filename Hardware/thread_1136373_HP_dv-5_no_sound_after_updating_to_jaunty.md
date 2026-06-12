---
title: "HP dv-5 no sound after updating to jaunty"
date: 2009-04-25
forum: Hardware
---

### Post by llama_attack on 2009-04-25
Hey, I've just updated to Jaunty, and I'm getting no sound whatsoever out of my laptop speakers. I've checked volume control and nothing is muted and the volume is right up. Is there any way of getting my speakers working again?

---

### Post by vanadium101 on 2009-04-25
same here. I've been using jaunty since beta and have tried to get sound with no result. the only time i had sound was when i installed the 2.6.29 kernel, but that was to slow to use.

---

### Post by dozepih on 2009-04-25
Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

---

### Post by llama_attack on 2009-04-25
YES! Thank you! That did the trick

---

### Post by JohnSHendryJr on 2009-05-09
There is also a typo in /etc/modprobe.d/alsa which reads:
options snd-hda-intel model=hp-dv5 enable_mis=1
and should be
options snd-hda-intel model=hp-dv5 enable_msi=1

---

### Post by mappas on 2009-05-11
I got sound problem too. I have an HP dv-5

This is how thhe alsa file looks

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/mod
probe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; :
 ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-o
ss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;
/sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq
-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu
10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq
 ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ;
: ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=hp-dv5 enable_msi=1




Is it ok?



  Thanx a lot

---

### Post by theromanone on 2009-05-27
> **dozepih said:**
> Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

Worked!! just had to do the 
killall pulseaudio

sudo alsa force-reload

pulseaudio -D

commands, log out, log in, and voila! thanks!!

---

### Post by 4feli on 2009-07-21
Hi. I've just installed 9.04 onto my HP dv-5 and have the same problem. But as a complete beginner I'm afraid I don't understand how to complete the solution.


'Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel'

er, how, where do I do this?

---

