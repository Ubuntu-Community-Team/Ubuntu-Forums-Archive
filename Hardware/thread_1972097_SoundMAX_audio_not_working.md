---
title: "SoundMAX audio not working"
date: 2012-05-03
forum: Hardware
---

### Post by gabetorvalds on 2012-05-03
Hello. 

I'm running 10.04 and have no audio. I checked alsa mixer and no channels ware muted. 
I don't get audio either via the spdif or the 3,5mm plugs. The integrated soundcard works fine on windows xp sp3 32bit, so the hardware is working. 

I ran this alsa info script and here's the output:
[http://pastebin.com/z2QejYD7](http://pastebin.com/z2QejYD7)
It has 1300lines so I'll only paste some cherry picks here. Pastebin has the full output.
As seen in the paste I'm running a Asus P5N-T Deluxe with NVIDIA nForce 780i SLI chipset. 

I only found this when I googled this:
[http://ubuntuforums.org/showthread.php?t=1738874](http://ubuntuforums.org/showthread.php?t=1738874)
The guys has the same problem and the chipset. No resolution.


> !!Linux Distribution
!!------------------

Ubuntu 10.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer INC.
Product Name:      P5N-T DELUXE
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    2.6.32-41-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff4000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:0f.1 0403: 10de:0371 (rev a2)
    Subsystem: 1043:8266


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


---

