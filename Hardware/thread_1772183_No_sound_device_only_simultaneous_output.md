---
title: "No sound device only simultaneous output"
date: 2011-05-31
forum: Hardware
---

### Post by w1d3 on 2011-05-31
I installed this sound driver manually "link at bottom" and after i rebooted all my devices disappeared i tried reinstalling alsa, pulseaudio etc. with no success .... O and im using Ubuntu Studio 11.04

[http://www.mediafire.com/?0abjqoxag0ey5h4](http://www.mediafire.com/?0abjqoxag0ey5h4)

---

### Post by w1d3 on 2011-06-01
can anyone help me ??

---

### Post by w1d3 on 2011-06-02
anyone ???

---

### Post by w1d3 on 2011-06-03
.....

---

### Post by lidex on 2011-06-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by w1d3 on 2011-06-04
[http://www.alsa-project.org/db/?f=9ca81368a7a100a53b04cf6ad834ef4f770af0d7](http://www.alsa-project.org/db/?f=9ca81368a7a100a53b04cf6ad834ef4f770af0d7)

---

### Post by lidex on 2011-06-04
OK. You need an alsa re-install.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Next post this info:
```
dpkg -l | grep "alsa"
```

---

### Post by z0Zor on 2011-06-05
hi , i am a new user of linux , 
I am also got this problem , i didnt resolve it , no sound in my earphone only the internal sound of my computer .
So i followed your instructions trying to solve this problem , but still the same .
This in the first command entered in the terminal :
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
This is the answer : [http://www.alsa-project.org/db/?f=120d994e19f179dcdf2648eaed71100ebe72fcca](http://www.alsa-project.org/db/?f=120d994e19f179dcdf2648eaed71100ebe72fcca)
I hope you will help me soon .
My configuration : Toshiba Satelite L650 , 4Mo Ram , 4Ghz


And sorry for my bad english .

---

### Post by w1d3 on 2011-06-05
> **lidex said:**
> OK. You need an alsa re-install.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```Next post this info:
```
dpkg -l | grep "alsa"
```

for me to post that I have a problem that means i tried everything i can find in google and that it didnt work xD anyways here is the output:
```
ii  alsa-base                             1.0.24+dfsg-0ubuntu1                              ALSA driver configuration files
ii  alsa-source                           1.0.24+dfsg-0ubuntu1                              ALSA driver sources
ii  alsa-tools                            1.0.24.1-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                        1.0.24.1-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                            1.0.24.2-0ubuntu6                                 Utilities for configuring and using ALSA
ii  alsamixergui                          0.9.0rc2-1-9                                      graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                       0.99.80-5build1                                   PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                     0.99.80-5build1                                   PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                        0.99.80-5build1                                   PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-jack                       0.99.80-5build1                                   PCM player designed for ALSA (JACK output module)
ii  bluez-alsa                            4.91-0ubuntu1                                     Bluetooth ALSA support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                         ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                                  GStreamer plugin for ALSA
ii  libclalsadrv2                         2.0.0-3                                           ALSA driver C++ access library
rc  libsdl1.2debian-alsa                  1.2.14-6.1ubuntu3                                 Simple DirectMedia Layer (with X11 and ALSA options)

```

---

### Post by lidex on 2011-06-05
OK. We'll need an updated alsa-info script.

---

### Post by w1d3 on 2011-06-05
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jun  5 22:39:25 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      4186                
Product Version:   Lenovo IdeaPad Y550             


!!Kernel Information
!!------------------

Kernel release:    2.6.38-8-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 17aa:3a0d
--
01:00.1 0403: 10de:0be2 (rev a1)
    Subsystem: 17aa:38ff


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw------- 1 root root 116,  1 Jun  6 01:36 /dev/snd/seq
crw------- 1 root root 116, 33 Jun  6 01:36 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
sha256_generic
cryptd
aes_i586
aes_generic
parport_pc
ppdev
dm_crypt
joydev
binfmt_misc
arc4
nvidia
iwlagn
iwlcore
mac80211
uvcvideo
videodev
cfg80211
psmouse
soundcore
ideapad_laptop
rc_rc6_mce
serio_raw
snd_page_alloc
sparse_keymap
ir_lirc_codec
lirc_dev
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
ir_nec_decoder
ene_ir
rc_core
lp
parport
tg3
ahci
video
libahci
uvesafb


!!ALSA/HDA dmesg
!!------------------

[   23.834402] type=1400 audit(1307313418.187:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=760 comm="apparmor_parser"
[   23.874058] snd: Unknown symbol unregister_sound_special (err 0)
[   23.874395] snd: Unknown symbol register_sound_special_device (err 0)
[   23.875935] snd_timer: Unknown symbol snd_info_register (err 0)
--
[   23.877243] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[   23.889381] snd: Unknown symbol unregister_sound_special (err 0)
[   23.889721] snd: Unknown symbol register_sound_special_device (err 0)
[   23.891231] snd_timer: Unknown symbol snd_info_register (err 0)


```

---

### Post by lidex on 2011-06-05
You should at this point boot into another kernel, preferably non-pae and see if you get sound.

---

### Post by w1d3 on 2011-06-06
yup i got the sound back now i need to figure out how to get it back in pae xD

---

