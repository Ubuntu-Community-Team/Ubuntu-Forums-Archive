---
title: "asus eee pc4g no soundcard"
date: 2014-03-28
forum: Hardware
---

### Post by pero2 on 2014-03-28
I got problem on my laptop with sound. I got alsa error no suitable mixer element found, snd_mixer_attach failed no such file or directory.
I try sudo aplay -l
Aplay: device_list:268: no soundcards found. Anybody some help Im using lubuntu, thank you.

---

### Post by Yellow Pasque on 2014-03-29
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by pero2 on 2014-03-29
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Sat Mar 29 13:52:58 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 13.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 13.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 13.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer INC.
Product Name:      701
Product Version:   x.x
Firmware Version:  0801   


!!Kernel Information
!!------------------

Kernel release:    3.11.0-18-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.27.2
Utilities version:  1.0.27.1


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  1 Mar 29 03:03 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Mar 29 03:03 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
arc4
ath5k
ath
mac80211
cfg80211
nls_iso8859_1
zram
vesafb
joydev
uvcvideo
videobuf2_vmalloc
psmouse
microcode
i915
videobuf2_memops
videobuf2_core
drm_kms_helper
lpc_ich
videodev
parport_pc
ppdev
drm
rfcomm
serio_raw
bnep
bluetooth
i2c_algo_bit
video
eeepc_laptop
mac_hid
sparse_keymap
lp
parport
usb_storage


!!ALSA/HDA dmesg
!!--------------



I got this info. But still no soundcard.

---

### Post by Yellow Pasque on 2014-03-29
Okay, so is the sound device enabled in the BIOS/UEFI? Does it show in lspci? (give output of lspci -k)

```
sudo update-pciids
lspci -k
```

---

### Post by pero2 on 2014-03-29
Thank you on time and help it was disabled in bios.

---

