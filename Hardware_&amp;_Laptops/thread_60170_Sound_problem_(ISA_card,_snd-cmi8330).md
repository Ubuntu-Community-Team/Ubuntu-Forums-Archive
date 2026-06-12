---
title: "Sound problem (ISA card, snd-cmi8330)"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by kajaman on 2005-08-26
Hi,
I have problem with my ISA CMI8330 sound card. On slackware/vector/fedora/whatever (with 2.6 kernels), when I do:

[COLOR=DimGray]#modprobe -v snd
#modprobe -v snd-cmi8330
[/COLOR]

the driver is loaded and I can use my sound card. But with Ubuntu (5.04 and 5.10 development branch too) this seems not to work. All I get is : 

[COLOR=DimGray]#modprobe -v snd
#modprobe -v snd-cmi8330
install modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
insmod /lib/modules/2.6.12-7-386/kernel/sound/isa/snd-cmi8330.ko
FATAL: Error inserting snd_cmi8330 (/lib/modules/2.6.12-7-386/kernel/sound/isa/snd-cmi8330.ko): No such device
FATAL: Error running install command for snd_cmi8330[/COLOR]

I bealieve that this is because kernel doesn't support ISA card autodetection (?) and I should pass arguments after #modprobe -v snd-cmi8330, like irq=something... But I'm not shure where to get this arguments and their values...

Any suggestions welcome :)

---

### Post by wvslkr on 2005-08-27
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)   Hope that helps you get it sorted.

GL :)

---

