---
title: "no mic on sony vaio vpcw12j1e"
date: 2010-03-10
forum: Hardware
---

### Post by suoko on 2010-03-10
i'm experiencing internal mic input problems on this netbook.
i have 2 input in pulseaudio (internal mic and external i guess) but none of them seems working.
i tried modifying /etc/modprobe.d/alsa-base.conf as follow:

options snd-hda-intel power_save=10 power_save_controller=N
->
options snd-hda-intel model=auto power_save=10 power_save_controller=N

and now i see one input source only and internal mic still doesn't work.

$ modinfo snd-intel8x0
filename:       /lib/modules/2.6.31-20-generic/kernel/sound/pci/snd-intel8x0.ko
license:        GPL
description:    Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     09B55E87B5564D9B98E15DB
alias:          pci:v000010B9d00005455sv*sd*bc*sc*i*
alias:          pci:v00001022d00007445sv*sd*bc*sc*i*
alias:          pci:v00001022d0000746Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000EAsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000DAsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000008Asv*sd*bc*sc*i*
alias:          pci:v000010DEd00000059sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000006Asv*sd*bc*sc*i*
alias:          pci:v000010DEd0000003Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000001B1sv*sd*bc*sc*i*
alias:          pci:v00001039d00007012sv*sd*bc*sc*i*
alias:          pci:v00008086d00007195sv*sd*bc*sc*i*
alias:          pci:v00008086d00002698sv*sd*bc*sc*i*
alias:          pci:v00008086d000027DEsv*sd*bc*sc*i*
alias:          pci:v00008086d0000266Esv*sd*bc*sc*i*
alias:          pci:v00008086d000025A6sv*sd*bc*sc*i*
alias:          pci:v00008086d000024D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000024C5sv*sd*bc*sc*i*
alias:          pci:v00008086d00002485sv*sd*bc*sc*i*
alias:          pci:v00008086d00002445sv*sd*bc*sc*i*
alias:          pci:v00008086d00002425sv*sd*bc*sc*i*
alias:          pci:v00008086d00002415sv*sd*bc*sc*i*
depends:        snd-ac97-codec,snd-pcm,snd,snd-page-alloc
vermagic:       2.6.31-20-generic SMP mod_unload modversions 586 
parm:           index:Index value for Intel i8x0 soundcard. (int)
parm:           id:ID string for Intel i8x0 soundcard. (charp)
parm:           ac97_clock:AC'97 codec clock (0 = whitelist + auto-detect, 1 = force autodetect). (int)
parm:           ac97_quirk:AC'97 workaround for strange hardware. (charp)
parm:           buggy_semaphore:Enable workaround for hardwares with problematic codec semaphores. (bool)
parm:           buggy_irq:Enable workaround for buggy interrupts on some motherboards. (bool)
parm:           xbox:Set to 1 for Xbox, if you have problems with the AC'97 codec detection. (bool)
parm:           spdif_aclink:S/PDIF over AC-link. (int)
parm:           enable:bool
parm:           joystick:int

---

### Post by suoko on 2010-03-13
bump

---

### Post by suoko on 2010-03-21
auto solved by installing 
linux-backports-modules-alsa-karmic-generic
linux-backports-modules-karmic

guess they should be installed by default

---

