---
title: "Sound problem (alsa-driver)"
date: 2011-03-25
forum: Hardware
---

### Post by marouane87 on 2011-03-25
Hi :)

I've just installed Xubuntu 10.10, and I'm having a problem as there's no sound :( (I installed previous ubuntu version before and the sound worked great)
I checked my CD of drivers and I found a folder named linux containing this folder: alsa-driver-0.9.2 (but I couldn't install it, I'm new and I don't know how to do that, I used the instructions but got some trouble...).
So I searched on google and I downloaded this package [http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip)
And I used the installer to install it (after decompressing it), but the installer gave some error too.

Please any idea how set set the sound?
Thank you :D

---

### Post by Yellow Pasque on 2011-03-25
Please run the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by marouane87 on 2011-04-02
> ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.RfB3IAX8HO/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : n


Your ALSA information is in /tmp/alsa-info.txt.GmuGMuVoaf




upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Apr  2 10:55:26 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INC.
Product Name:      MS-6728
Product Version:   2.00


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


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


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24d5 (rev 02)
	Subsystem: 1462:0080


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



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
nouveau
ttm
drm_kms_helper
drm
intel_agp
i2c_algo_bit
ppdev
agpgart
shpchp
parport_pc
psmouse
serio_raw
lp
parport
usbhid
r8169
hid
floppy
mii


!!ALSA/HDA dmesg
!!------------------







On the other hand I've notices another problem, after installing alsa-driver linuxtant, I changed some stuff on the mixer and the sound worked, but I had no more internet connection, today, I deleted the alsa-driver linuxtant, the connection is back but I have no sound. Any help with this compromise please?

Thank you very much :D

---

### Post by lidex on 2011-04-02
A botched linuxant install would be my guess. Try re-installing alsa. Using a Terminal
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by marouane87 on 2011-04-04
Thank you very much for you answers :P
I reinstalled Xubuntu and installed "ubuntu-resricted-plugins", all was fine, but I don't know why after rebooting today I had no connection (I'm using a wired connection). I appreciate if you can help me here or should I start a new thread?

---

### Post by lidex on 2011-04-05
I would suggest asking over here:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by Marcelush on 2011-04-05
I've got the same problem, but the difference is that you have a cd with drivers , i don't! but this thread solved my problem. Thank you.

---

