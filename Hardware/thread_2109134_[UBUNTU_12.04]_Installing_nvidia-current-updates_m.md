---
title: "[UBUNTU 12.04] Installing nvidia-current-updates made the audio to stop working"
date: 2013-01-26
forum: Hardware
---

### Post by ihtfp on 2013-01-26
Hi all,


I've spent the whole afternoon trying to solve an issue with my config but definitely I have no clue anymore.


Config : Shuttle XS35GTV2
[SIZE=1][FONT=courier new]$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)[/FONT][/SIZE]



The sound was previously working, but I installed  nvidia-current-updates to have the OpenGL enabled (instead of nouveau  driver). From this moment, the sound stopped working.


What I can say is the driver hda-intel is used for both card.
Since I suspected it was the problem, I tried a lot of combinations of  what I found from others posts' to disable the Nvidia audio only but  nothing solved the problem. I mainly changed the  /etc/modprobe.d/alsa-base.conf but also ~/.asoundrc


Please find my dirty /etc/modprobe.d/alsa-base.conf below (combinations of disabling / inverting / whatever) :

[SIZE=1][FONT=courier new]install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install  snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && {  /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install  snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install  snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install  snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install  snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2



# options snd slots=,snd-hda-intel
# options snd-hda-intel enable_msi=0 probe_mask=0,0
# options snd-hda-intel model=laptop
# options snd-hda-intel position_fix=1 enable=yes
# options snd-hda-intel model=generic


alias char-major-116 snd

#alias snd-card-0 snd-hda-intel
#alias snd-card-1 snd-hda-intel
#alias snd-card-2 snd-usb-audio

# Change this line
#options snd cards_limit=1

#  slots=snd-hda-intel

# Remove or comment out the lines that had "index"
#options snd-hda-intel index=0
#options snd-usb-audio index=2

#options snd-hda-intel index=0 model=auto probe_mask=1
#options snd-hda-intel index=0 enable_msi=1

#options snd-hda-intel index=1 model=auto probe_mask=2
#options snd-hda-intel index=1 enable_msi=1
#options snd-hda-intel index=1 single_cmd=1
#options snd-hda-intel index=1 bdl_pos_adj=128

# options snd slots=,snd-hda-intel
#options snd-hda-intel model=auto probe_mask=1
#options snd-hda-intel enable_msi=1

# options snd slots=snd-hda-intel,nd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-i
options snd-hda-intel model=auto enable=0 index=0
options snd-hda-intel enable=1 index=1[/FONT][/SIZE]

Please also find attached the complete output of the ALSA diagnostic tool ([ATTACH]230678[/ATTACH]) :
[FONT=courier new][SIZE=1]$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh[/SIZE][/FONT]


Have you got any suggestion please ?



Thanks,

---

