---
title: "No sound with ALC662 / intel HDA"
date: 2008-11-02
forum: Hardware
---

### Post by Melstar on 2008-11-02
Hi,

I've got a sound problem with a Packard-bell Easynote BG 

(Ubuntu 8.10, kernel 2.6.27-7-generic, CPU Intel Core 2 Duo 2.5 GHz)

**uname -a**
Linux PBBG47-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

**lspci | grep Audio**
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
 Subdevices: 0/1
 Subdevice #0: subdevice #0

Alsa drivers installed and loaded, no channel's muted, but [B]there is no
sound.[/B]

Also, i have PulseAudio appearing as my card and chip in AlsaMixer:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio
&#9474; Chip: PulseAudio
&#9474; View: [Playback] Capture  All
&#9474; Item: Master


Any idea?

---

### Post by mfallavol on 2008-11-29
I'm wondering if you ever figured this one out.  I have a relatively new Intel Mini-ITX motherboard (Atom processor) with the ALC662 and it is behaving exactly the same way you describe.

   -- Mike

---

### Post by Melstar on 2008-11-30
No, I still haven't figured it out. 

The only trail I've got so far is that someone told me if you self-compile the new Release Candidate version of the kernel, that is 2.26.8 RC6 as of today, the sound should be working fine....

Good luck, lemme know if you find out anything else.

Thx

---

### Post by hardkaare on 2008-11-30
Hey there

I having scratching sound, and no sound from my subwoofer :-(

got a 2.1 surround system in my laptop.

I found this bug, maybe its related to our problem?

Take a look at this bug:
[https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

laptop 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

modinfo snd_hda_intel
filename:       /lib/modules/2.6.27-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     1F9333782C7C7E6EF287F87
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
vermagic:       2.6.27-10-generic SMP mod_unload modversions 
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
****

---

### Post by Stretchnuts on 2009-11-18
Hey, I just figured out how to enable my intel hda soundcard.

I ran the following command in terminal:

sudo modprobe snd_hda_intel

works like a charm now ;)
Hope it works for you as well!

---

