---
title: "suddenly lost sound in ubuntu 9.04"
date: 2009-08-18
forum: Hardware
---

### Post by zepita on 2009-08-18
Hi, I have lost sound playback today when I booted up the computer.

The os is ubuntu 9.04 i386 installed in a lenovo r61i laptop.


```
id:	
multimedia
description: 	Audio device
product: 	82801H (ICH8 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
module	=	snd_hda_intel
```

Any clues? I have tested all sound servers and no sound output, but the progress bar works as if my built-in speakers would be dead o low volume or muted, but, with a headset or external speakers the issue persists.

Thanks

---

### Post by utnubuuser on 2009-08-18
I think maybe a recent kernel or other change has messed the thinkpad sound configuration.  The sound on my x31 went recently too, - got it back by following this how-to:> [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")

---

### Post by zepita on 2009-08-18
> **utnubuuser said:**
> I think maybe a recent kernel or other change has messed the thinkpad sound configuration.  The sound on my x31 went recently too, - got it back by following this how-to:

Thanks!! that worked for me. Apparently after the update, the PCM volume got muted somehow.

---

