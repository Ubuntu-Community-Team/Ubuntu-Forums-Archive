---
title: "Getting sound from Rig Kontrol 2"
date: 2009-05-16
forum: Hardware
---

### Post by Nareto on 2009-05-16
Hello, i'm trying to get sound from my [Rig Kontrol 2]("http://www.native-instruments.com/index.php?id=rigcontrol2_us") from Native Instruments - it's a pedal board for guitar with a sound card integrated. Native Instruments has helped development of an alsa driver for it's devices: snd-caiaq. I've modprobed "snd-usb-caiaq" but still no sound. 

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 17cc:1969 Native Instruments RigKontrol2
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
...
```

```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc400000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfc010000 irq 17
 2 [default        ]: snd-usb-caiaq - 
                        (serial , usb-0000:00:1d.7-6)

```

But nor in System->Preferences->Sound nor right clicking on the volume thing in the top right screen corner and choosing Preferences can I see the sound card - i see only the onboard one.

I tried using the device on Vista-virtual box guest on my Ubuntu- where i have propietary drivers installed, and it behaves strangely: it is detected correctly by the system, but Guitar Rig (the software that comes with it) won't show any input, it will only show when i press buttons but it won't even make the corresponding action. This could be an issue with Virtual Box though.

I am not sure what should i do. By the way, regarding [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-caiaq]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-caiaq") i can't understand if the information of sections 3-5 is specific to this module or is general. Should i follow all these steps or am i missing something easier?
As suggested in section 2 i tried 
```
$ modinfo soundcore
filename:       /lib/modules/2.6.28-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     73D4C7B18BCDAF17EE3F9B5
depends:        
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 

```
i even tried modprobing it without any change.
Any help greatly appreciated.

---

### Post by Nareto on 2009-05-16
Update: If i start jack and then Patchage, i can see an "External Midi" box that disappears when i unplug Rig Kontrol (the sound card in it has midi in/out; pedals and switches don't send midi events themselves though). 
This seems to me like an issue with the alsa driver...

---

### Post by Nareto on 2009-05-18
bump

---

### Post by Nareto on 2009-05-19
bump

---

### Post by Nareto on 2009-05-20
anyone?

---

