---
title: "No sound Ubuntu 9.04 after online update"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by mbogevik on 2009-09-13
After a online update on Friday 11 of September with 11 days update files my sound did not work anymore, just a low crackling can be heard.

My mainboard is Asus P5Q SE2, in "user.log.0" I found this :

Sep 11 23:58:08 Morten pulseaudio[3427]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Sep 12 00:10:17 Morten pulseaudio[5632]: pid.c: Stale PID file, overwriting.

Any suggestions ?

---

### Post by norm7446 on 2009-09-13
Install all Gstreamer plugins. This worked for me.

---

### Post by newsoft on 2009-09-13
> Install all Gstreamer plugins. This worked for me.


Thanks for this :)

---

### Post by mbogevik on 2009-09-18
This does not work for me.  I have also tried other suggestions I have found with no luck.  However, I see that many have problems with Intel HD sound chipset.

In  /etc/modprobe.d/alsa-base.conf there is a lot of strange settings, "Workaround at bug #499695" does not make me relax at all...

Ubuntu says my main board has a bios bug and that it make a workaround, but this Ubuntu also said when sound was working.

I may not have mention that sound have been working in XP all the time ?

My /etc/modprobe.d/alsa-base.conf : 

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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

---

### Post by mbogevik on 2009-09-23
It seems that update have set PCM sound in mixer close to zero or off.  The most easy reason I did not think of checking :)  This way I will not know if install Gstreamer plugins did help or not.

---

### Post by mjwood on 2009-10-04
I know this is solved, but I wanted to post a confirmation.

I had the same symptoms (board, audio, and log).

I checked the alsamixer settings first. PCM was at zero for me. I increased it to 72, but I still had no sound.

I re-installed gstreamer and audio began to play.

---

