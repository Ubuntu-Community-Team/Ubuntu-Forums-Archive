---
title: "Asus m50VM - a1 - Sound not working"
date: 2009-07-29
forum: Hardware
---

### Post by been_1990 on 2009-07-29
Hi guys! This is my 3rd thread on my problem. None of the previous were answered. I've already followed several, almost all, tutorials and guides about sound problems on the Asus m50 series. But to no avail.
Here is my info:

```
!!################################
!!ALSA Information Script v 0.4.57
!!################################

!!Script ran on: Wed Jul 29 12:51:24 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      
Product Name:      


!!Kernel Information
!!------------------

Kernel release:    2.6.28-11-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.18
Utilities version:  1.0.18


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

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1043:1893


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:217: no soundcards found...

ARECORD

arecord: device_list:217: no soundcards found...

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
ppdev
bridge
stp
bnep
input_polldev
joydev
sbp2
lp
parport
arc4
ecb
uvcvideo
ath9k
compat_ioctl32
mac80211
psmouse
videodev
iTCO_wdt
pcspkr
serio_raw
video
sdhci_pci
sdhci
nvidia
v4l1_compat
intel_agp
iTCO_vendor_support
cfg80211
asus_laptop
output
agpgart
btusb
led_class
ohci1394
ieee1394
r8169
mii
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

```

```
**aplay -l**
aplay: device_list:217: no soundcards found...

```

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 03)
        Subsystem: ASUSTeK Computer Inc. Device 1893
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

```

I think that's all. Please help me with this.:D

---

### Post by been_1990 on 2009-08-03
So... five days!! No response. Why?

---

