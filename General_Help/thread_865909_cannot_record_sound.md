---
title: "cannot record sound"
date: 2008-07-21
forum: General Help
---

### Post by beN..87 on 2008-07-21
i'm trying to get up and running recording what is coming out of my speakers, i've tried using the ubuntu sound recorder and gtl desktop capture and also audacity, i can't seem to get anywhere with this

i'm not trying to record from microphone, but what is playing on the web ect

heres some info 

audacity recognises inputs

ALSA - default
OSS /dev/dsp
ALSA: HDA ATI SB: ALC262 Analog (hw:0,0)


i have tried selecting inputs  as digital, capture, Mic boost PCI , and the like  - and yet i cant seem to get anywhere

heres my sound card


description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

any ideas as to how to go about getting going with this?

thanks in advance

---

### Post by Dave Otter on 2008-07-21
Try this

   Right click Icon on tool bar to open  volume control

      Edit.>Preferences    -   ensure line in is ticked

                  May help?

---

