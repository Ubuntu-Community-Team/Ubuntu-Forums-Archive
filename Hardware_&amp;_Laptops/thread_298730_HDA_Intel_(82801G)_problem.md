---
title: "HDA Intel (82801G) problem"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by Uther on 2006-11-13
Hi

Whenever the sound is activated on an Intel HDA (82801G) sound card there is a high-pitched noise. The problem did not exist in Debian etch, so presumably it's a problem with the drivers provided with Ubuntu.

This is on a Packard Bell Easynote MX laptop.

Any help would be appreciated.

lspci output:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

modinfo snd-hda-intel:
filename:       /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd-page-alloc,snd-hda-codec,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
srcversion:     31CA0C84834DEE3882349D3
parm:           enable:bool
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)

---

### Post by Uther on 2006-11-14
bump

---

### Post by Uther on 2006-11-19
bump

---

### Post by Uther on 2006-11-28
bump

---

### Post by ReaderRat on 2006-11-28
Have you tried (re)installing the alsa driver?
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by thnogueira on 2007-02-19
I'm having the same problem. Is there some workaround for this?

---

### Post by mikewhatever on 2007-02-19
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

as suggested above, reinstall the driver

---

### Post by thnogueira on 2007-02-19
EDIT: Sorry guys, the instructions provided by the above link have solved my troubles (alsa 1.0.14rc2) . I'd fogot to add the line to alsa-base files.

Thank you all.


Neither reinstalling the driver nor following the instructions that the link provides work for me. Any other suggestions? I have an Asus A8JP notebook. Is it possible to be related with ACPI problem? something like DSDT file?

---

