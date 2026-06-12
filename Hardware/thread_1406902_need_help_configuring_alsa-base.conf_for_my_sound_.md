---
title: "need help configuring alsa-base.conf for my sound cards please"
date: 2010-02-14
forum: Hardware
---

### Post by kronictokr on 2010-02-14
this is what my sound card setup looks like

laptop:~$ head -n 1 /proc/asound/card0/codec*
Codec: IDT 92HD75B3X5
laptop:~$ head -n 1 /proc/asound/card1/codec*
Codec: ATI RS690/780 HDMI
laptop:~$ head -n 1 /proc/asound/card2/codec*


/etc/modprobe.d/alsa-base.conf

looks like this

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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

id just like to make sure evrything is properly read in my os. even though i have full sound capabilities through all my outputs. any help would be greatly appreciated, tx in advance

this thread has some input on the subject, there are slight variances, depending on hardware, thats where i need help

would adding these two lines at the end of alsa-base.conf be right?

options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv6


also, would like to know if you see anything else i should change in there, let me know if you need more info ,

---

### Post by bherrmann7 on 2010-04-13
I've just installed Lucid Lynx (beta2) on with the Intel "92HD75B3X5" sound in a Pavilion dv8t, and it plays sound through both the speakers and through the two headphone jacks.   When plugging in headphones, the laptop speakers don't turn off.   I've tried running alsamixer to adjust only the speakers, but there doesnt appear to be a control for just the speakers and not the head phones.

---

### Post by linuxopjemac on 2010-08-29
sorry wrong thread...

---

