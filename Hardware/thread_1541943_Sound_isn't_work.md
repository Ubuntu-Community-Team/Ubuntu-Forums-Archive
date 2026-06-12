---
title: "Sound isn't work"
date: 2010-07-29
forum: Hardware
---

### Post by dtphong_1989 on 2010-07-29
Hi everyone. My have a problem about sound driver. My laptop is Sony Vaio VPCEB190X. 

This's information my sound: 

Output lspci -v:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
   Subsystem: Sony Corporation Device 9071
   Flags: bus master, fast devsel, latency 0, IRQ 22
   Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel
```Output aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Plz help me. Thank u:(:(:(:(:(

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Jul 29 15:08:57 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEB19FX


!!Kernel Information
!!------------------

Kernel release:    2.6.32-21-generic-pae
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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6000000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 104d:9071


```[http://www.alsa-project.org/db/?f=c168e8cbe0cd1125b578a8be79b61c6c8443da7c](http://www.alsa-project.org/db/?f=c168e8cbe0cd1125b578a8be79b61c6c8443da7c)

---

### Post by dtphong_1989 on 2010-07-30
Nobody know???

---

### Post by dtphong_1989 on 2010-07-30
Help me

---

### Post by viking350 on 2010-07-30
how did you get ubuntu did you install it with wubi?

---

### Post by viking350 on 2010-07-30
how did you get ubuntu did you install it with wubi??

---

### Post by dtphong_1989 on 2010-07-30
> **viking350 said:**
> how did you get ubuntu did you install it with wubi??

No, I installed Ubuntu through Live CD. By the way, I can get sound working in Windows 7.

---

### Post by Yellow Pasque on 2010-07-30
It is fixed in later versions of ALSA: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448?comments=all)

---

