---
title: "No Audio"
date: 2011-07-06
forum: Hardware
---

### Post by PushStart on 2011-07-06
I'm a Linux newb, can't get my audio to work. Works in Windows 7. Not sure what info is needed to help but other people seem to be posting [this thing]("http://www.alsa-project.org/db/?f=22d069afb6709f42aef7f39178f04c5af7e6ce4f"). Thanks.

---

### Post by lidex on 2011-07-06
You made an edit to alsa-base.conf. Please remove that then re-install alsa using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by PushStart on 2011-07-12
Still no sound. Sorry for the late response, been very busy. 

[http://www.alsa-project.org/db/?f=b3209988784d54feda2230d6088f4ccdea0dcdde](http://www.alsa-project.org/db/?f=b3209988784d54feda2230d6088f4ccdea0dcdde)

---

### Post by lidex on 2011-07-12
What are these outputs please:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d
```

---

### Post by DHAines56 on 2011-07-12
I had the same problem, I don't know what I did but just check the ALSA Mixer in terminal 

```
alsamixer
```This will come up with the ALSA Mixer, check to make sure it's using the right soundcard and that it's not muted.

---

### Post by PushStart on 2011-07-16
**cat /etc/modprobe.d/alsa-base.conf # autoloader aliases**:
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
options snd-hda-intel probe_mask=1 model=auto

options snd-hda-intel model=auto

---------------------------------------------------------------------------------
**ls /etc/modprobe.d**:
alsa-base.conf           blacklist-framebuffer.conf   oss4-base.conf
blacklist-alsa.conf      blacklist-modem.conf         oss4-base_noALSA.conf
blacklist-ath_pci.conf   blacklist-rare-network.conf  oss4-base_noOSS3.conf
blacklist.conf           blacklist-watchdog.conf
blacklist-firewire.conf  fglrx.conf

---

### Post by lidex on 2011-07-16
Open for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove these lines:
```
options snd-hda-intel probe_mask=1 model=auto
options snd-hda-intel model=auto

```
Save. Close.
Now follow the link in my sig to upgrade alsa to latest version.

---

