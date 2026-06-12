---
title: "Jaunty: Gateway FX6831 Sound Issues....still :("
date: 2009-05-12
forum: Hardware
---

### Post by Fluffy13 on 2009-05-12
Laptop Model: Gateway FX6831
Operating System: Ubuntu Jaunty 9.04

So im another user with an Intel HDA Soundcard that isnt working in Jaunty. I had no issues at all in hardy or intrepid. When i upgraded i did a clean install with all updates, and had no sound. I followed thread after thread and after a few hours i somehow managed to get my sound working through my headphones but still not my speakers.

I tolerated this because i had headphones and i NEED music to work (i'm a webdesigner and programmer among other things, im sure you understand) or i can't focus. Well the stupid dog ate my headphones so here we are. I don't know exactly what you need from me to get the picture of everything i have done, so please ask me and im happy to provide anything you need including my left arm to get this working.

I know the speakers work, i tested in Windows 7 just to be sure. Nothing is musted. I have tried muting the headphones, changing the device options, editing files, updating pulseaudio and alsa, tried the mixer in console, everything appears solid.

I'm using Amarock (1.4 hate the new one) but have tested in audacity, audacious, and tuxguitar so i know it isnt a program issue.

**lspci:**
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


**alsa-base.conf:**

Tried various configurations i found. Nothing worked.

> 
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
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

**options.conf:**

> 
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=3stack

---

### Post by Fluffy13 on 2009-05-12
Tried all the possible fixes i can seem to find. Even those for the HP dv4 series. Nothing is working. I hate to go back to intrepid over this because i like the changes jaunty brings but i mean...

---

### Post by Fluffy13 on 2009-05-13
Nobody?

---

### Post by Fluffy13 on 2009-05-15
Well it stinks but i guess im just going back to intrepid since nobody seems to have even a guess what else may fix the issue.

---

### Post by Fluffy13 on 2009-05-23
Any chance that the 64 bit version will work? This is making me insane

---

### Post by Fluffy13 on 2009-05-23
no such luck....

---

