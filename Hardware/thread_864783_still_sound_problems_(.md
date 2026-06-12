---
title: "still sound problems :("
date: 2008-07-20
forum: Hardware
---

### Post by vaidas on 2008-07-20
hey , i am new to linux and ubuntu
i read the recent post about it that solved most of the peoples problems but i can't fix mine ;(

i've got realtek (ALC880) sound card.
when i installed ubuntu 8.04 i could hear the sound from the speakers but the headphones and micro did not work.
downloaded realtek realtek-linux-audiopack-5.04 and installed it manually
b. ./configure
c. make
d. make install
e. ./snddevices

and added to /etc/modules
snd-hda-intel
snd-atiixp
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-xxxx
# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
restarted the machine. now neither the speakers nor the headphones work
when i switch on the alsamixergui i can manage every part of it except the "head" part.

i tried adding lines to modprobe.d/alsa-lib
but it does not change anything.
please help!

my alsa-lib is currently like this:
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by silvanus2005 on 2008-07-20
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Take a look at this thread, might find something helpfull.

---

### Post by vaidas on 2008-07-21
Hey, thanks for the link, but it didn't really help me much. is there any way to know exactly what i need and how i install it? 
living without me favourite music is hell, and absolutely no sound comes out of this machine...:confused:

---

### Post by silvanus2005 on 2008-07-22
I don`t know what your problem might be.I also have a Realtek sound card on my laptop, but it`s working out of the box, including microphone and headphones.

---

