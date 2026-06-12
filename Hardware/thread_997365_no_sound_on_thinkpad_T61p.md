---
title: "no sound on thinkpad T61p"
date: 2008-11-29
forum: Hardware
---

### Post by maikelmeyers on 2008-11-29
Hi,

I've installed Ubuntu Intrepid Ibex and the sound worked well, but then after a restart there was no sound anymore and I don't get it to work. Master and PCM are at 100 percent, the driver is loaded correctly. Can you give me advice what I can try? What kind of information do you need?

Thanks a lot
Maik

---

### Post by maikelmeyers on 2008-11-30
no ideas? Or did I something wrong in my description? I've read several threads now to ubuntu/thinkpad sound problems, but nothing helps, because everything is set up correctly. It behaves as if the volume is set to 0 percent. This is so frustrating. It is now the 3th ubuntu version on my computer and since hardy and pulseaudio there are always problems with sound and it is getting worse with every version. Maybe I should go back to Gutsy. I cannot imagine why sound works (and also works after restart) and then after doing nothing and another restart suddenly the sound is gone. 

```

uname -a
Linux rechenknecht 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

 lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

modinfo snd_hda_intel
filename:       /lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     B3799F6F8BD0B54DDBBF5D1
alias:          pci:v00006549d00001200sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD7sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD6sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD5sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC3sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC2sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC1sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias:          pci:v000010DEd00000777sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000776sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000775sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000774sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA48sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA40sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA38sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA30sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA28sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA20sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA18sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA10sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA08sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000970Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00003B56sv*sd*bc*sc*i*
alias:          pci:v00008086d00003A6Esv*sd*bc*sc*i*
alias:          pci:v00008086d00003A3Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d00002911sv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

---

### Post by emphyrio on 2008-12-05
I am experiencing the same issue.  I also have a thinkpad t61p.  At this point I don't know what's up, but just wanted to let you know you are not alone.

---

### Post by emphyrio on 2008-12-05
Silly me.  I just ran latest update and my thinkpad t61p has sound again.

---

