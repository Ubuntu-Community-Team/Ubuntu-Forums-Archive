---
title: "Ubuntu version 11.10  No sound Acl883 Realtek Hd Audio"
date: 2012-01-27
forum: Hardware
---

### Post by ketan711988 on 2012-01-27
I have no audio on my system, that is asus m2a-vm motherboard.Tried installing the drivers from realtek but they turned up an error. Here's what the alsa script returned.Also are there any driver for the ati x1250 chipset? I have to run unity 2d or the window movements are slow and lag sometimes.



!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Jan 27 10:19:51 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    3.0.0-12-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.20
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


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1043:8249


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
snd-hda-intel: model=generic
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
snd-hda-codec-realtek: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  1 Jan 27 15:28 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Jan 27 15:28 /dev/snd/timer


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
bnep
rfcomm
bluetooth
binfmt_misc
ppdev
radeon
asus_atk0110
parport_pc
k8temp
ttm
drm_kms_helper
drm
sp5100_tco
soundcore
i2c_algo_bit
i2c_piix4
ati_agp
shpchp
lp
parport
usbhid
hid
pata_atiixp
r8168
ahci
libahci


!!ALSA/HDA dmesg
!!------------------

[    8.615720] [drm] Connector 2:
[    8.615721] [drm]   HDMI-A
[    8.615722] [drm]   HPD2
--
[    8.911827] 
[    8.911832] radeon 0000:01:05.0: HDMI-A-1: EDID block 0 invalid.
[    8.911835] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[    8.922248] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID

---

### Post by ketan711988 on 2012-02-12
anyone?

---

