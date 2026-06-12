---
title: "No sound through HDMI port to TV."
date: 2010-01-04
forum: Hardware
---

### Post by cajual on 2010-01-04
UPDATE:

> 
Just ran the alsa-info tool:

[http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0](http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0)

Can anyone discern why I have no snd-*hdmi* module loaded?


```

cajual@cajual-laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

cajual@cajual-laptop ~ $ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC272 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```Everything is unmuted in **alsamixer** and I have tried every variation in the sound setup that is possible (from Analog to Digital).  As far as I can tell, my HDMI port is through the nVidia graphics controller, and in **sysinfo** (from the synaptic package manager) nVidia shows up as the sound controller, but Ubuntu or Alsa forces it all through Intel.  Something is amiss and I just can't figure it out.

Any advice?

PS: It is an nVidia GT 230M.

---

### Post by cajual on 2010-01-05
Just some extra information...

```

cajual@cajual-laptop ~ $ lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at db400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
    Subsystem: Toshiba America Info Systems Device ff15
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by cajual on 2010-01-05
```

cajual@cajual-laptop ~ $ cat /proc/asound/
card0/   cards    hwdep    meminfo  NVidia/  pcm      timers   
card1/   devices  Intel/   modules  oss/     seq/     version 

```

```

cajual@cajual-laptop ~ $ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdb400000 irq 31
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd3000000 irq 32

```

```

cajual@cajual-laptop ~ $ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 1]: hardware dependent
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 10: [ 1- 3]: hardware dependent
 11: [ 1- 2]: hardware dependent
 12: [ 1- 1]: hardware dependent
 13: [ 1- 0]: hardware dependent
 14: [ 1]   : control

```

```

cajual@cajual-laptop ~ $ cat /proc/asound/card*/codec#* | grep Codec
Codec: Realtek ALC272
Codec: LSI ID 1040
Codec: Nvidia ID a
Codec: Nvidia ID a
Codec: Nvidia ID a
Codec: Nvidia ID a

```

---

### Post by cajual on 2010-01-05
Lastly,

```

cajual@cajual-laptop ~ $ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan  4 2010 for kernel 2.6.31-14-generic (SMP).

```

---

### Post by cajual on 2010-01-05
[COLOR=Red][B]I just learned that my chipset ICH9 is not supported by ALSA!!
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)
[/B] 
Is there a patch?[/COLOR]

---

### Post by cajual on 2010-01-05
Just ran the alsa-info tool:

[http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0](http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0)

Can anyone discern why I have no snd-*hdmi* module loaded?

---

### Post by cajual on 2010-01-06
Bump

---

### Post by cajual on 2010-01-07
Help?  Anyone?

---

