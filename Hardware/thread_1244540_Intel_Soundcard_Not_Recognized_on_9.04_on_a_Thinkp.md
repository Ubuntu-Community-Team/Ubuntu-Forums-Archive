---
title: "Intel Soundcard Not Recognized on 9.04 on a Thinkpad"
date: 2009-08-19
forum: Hardware
---

### Post by Shidash on 2009-08-19
[FONT=Verdana]Hello,
I am new to Ubuntu and I have been trying to solve this problem for several hours now with no luck. I have gone through all sorts of tutorials and tried modifying /etc/modprobe.d/alsa-base. 

However, this appears to be a driver issue. The driver is not showing up on my ALSA Information Script-

[/FONT]!!################################
!!ALSA Information Script v 0.4.57
!!################################

!!Script ran on: Thu Aug 13 19:07:15 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      7448CTO


!!Kernel Information
!!------------------

Kernel release:    2.6.28-14-generic
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
    Subsystem: 17aa:20f2


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=laptop-eapd
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=laptop-eapd


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
i915
binfmt_misc
drm
ppdev
bridge
stp
bnep
input_polldev
lp
parport
arc4
ecb
iwlagn
iwlcore
uvcvideo
thinkpad_acpi
compat_ioctl32
video
psmouse
videodev
led_class
pcspkr
mac80211
output
serio_raw
v4l1_compat
iTCO_wdt
iTCO_vendor_support
soundcore
nvram
intel_agp
agpgart
btusb
cfg80211
e1000e
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

[FONT=Verdana][http://www.alsa-project.org/db/?f=53070191af536f45b47fcd55d4c837633a9a656a](http://www.alsa-project.org/db/?f=53070191af536f45b47fcd55d4c837633a9a656a)

I also have not been able to find the proper sound driver or any fixes that worked to any extent.
[/FONT]

---

### Post by ajgreeny on 2009-08-19
In terminal run ```
sudo lshw -C multimedia
``` and see what that has to say about the card and driver.

---

### Post by Yellow Pasque on 2009-08-19
You don't even have a driver loaded. It's hard to tell if that was the case originally or as a result of your modifications.

Try:
```
sudo modprobe snd-hda-intel
```

If that doesn't work, please post any error output. Also, I would suggest you try the alsa info script in a LiveCD environment.

---

### Post by Shidash on 2009-08-24
sudo lshw -C multimedia outputs
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

I do get warnings when I type in sudo modprobe snd-hda-intel
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

How would I go about fixing these files? Do these seem like they are most likely causing my sound issue?

---

