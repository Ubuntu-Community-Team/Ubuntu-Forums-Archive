---
title: "i need to know about alsa-base"
date: 2008-09-01
forum: General Help
---

### Post by Uchiha_madara on 2008-09-01
what are the keywords that can i use it with 'options'
while adding new module to the alsa-base file in :

> sudo nano /etc/modprobe.d/alsa-base

in the last line i need to add 'snd-hda-intel' to the kernel :

> options snd-hda-intel

i need what are the keywords i need to write to make the sound work

i hope that my question is clear ????:guitar::guitar::guitar::guitar:

---

### Post by Zorael on 2008-09-01
```
$ modinfo snd-hda-intel
filename:       /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     788923729243CAF84C8707E

...

depends:        snd-pcm,snd-page-alloc,snd,snd-hwdep
vermagic:       2.6.24-21-generic SMP mod_unload 586
parm:           **power_save**:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           **index**:Index value for Intel HD audio interface. (array of int)
parm:           **id**:ID string for Intel HD audio interface. (array of charp)
parm:           **enable**:Enable Intel HD audio interface. (array of bool)
parm:           **model**:Use the given board model. (array of charp)
parm:           **position_fix**:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (array of int)
parm:           **probe_mask**:Bitmask to probe codecs (default = -1). (array of int)
parm:           **single_cmd**:Use single command to communicate with codecs (for debugging only). (bool)
parm:           **enable_msi**:Enable Message Signaled Interrupt (MSI) (int)
parm:           **power_save_controller**:Reset controller in power save mode. (bool)
```
Just make sure that you have everything unmuted before starting to tinker with model settings (which is likely what you otherwise need to do.) Run **alsamixer** in a terminal.

As for models, please see [http://ubuntuforums.org/showthread.php?p=4869458#post4869458](http://ubuntuforums.org/showthread.php?p=4869458#post4869458), as well as [http://backports.ubuntuforums.com/showpost.php?p=4869649&postcount=2](http://backports.ubuntuforums.com/showpost.php?p=4869649&postcount=2).

---

