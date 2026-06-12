---
title: "Internal speakers - no sound"
date: 2010-04-30
forum: Hardware
---

### Post by Skyline649 on 2010-04-30
Hello,
Today I've installed the new distribution ( LUCID) of Ubuntu , and everything seems to be ok for the moment , except the sound of the internal speakers of my laptop.

That's the model of my sound card:

[SIZE=3]**Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller**[/SIZE]

---

### Post by dino99 on 2010-04-30
install from synaptic: paprefs and gnome-alsamixer and tweak settings as you need (apps sound)

if that dont work:

sudo gedit /etc/modprobe.d/alsa-base.conf

and add at this end : options snd-hda-intel model=auto

"auto" can be replaced with the exact alsa model, follow the link below:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Skyline649 on 2010-04-30
When I enter in the terminal "sudo gedit /etc/modprobe.d/alsa.conf" , it's EMPTY , so I think I don't have the driver at all, and I think i should use ALSA not PULSE , if you know how to install everything that is needed for a normal use of ALSA , tell me how to install it properl, because I already had this problem with the speakers , and by the way i've installed the file from the Synaptic, but nothing happens

---

### Post by dino99 on 2010-04-30
may be you can read or copy/paste and if you are too lazy to search yourself i dont care its your problem

---

### Post by peepingtom on 2010-05-01
Do the speakers work when you're using a Lucid Live CD?

---

### Post by Skyline649 on 2010-05-03
That's the output of sudo gedit /etc/modprobe.d/alsa-base.conf:

Now  I have sound with my stereo system when I plug in the cable into the jack ,and micro too , but internal still nothing

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
options snd-hda-intel model=auto
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

---

