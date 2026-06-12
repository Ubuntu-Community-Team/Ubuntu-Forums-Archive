---
title: "laptop build-in sub woofer"
date: 2008-12-01
forum: Hardware
---

### Post by atomizer on 2008-12-01
Hi,

I just bought a new laptop (HP dv7 1110ed) with a build-in subwoofer.

Is there a way to get the subwoofer working under Linux?

my soundhardware (lshw -C sound)

  *-multimedia            
       description: Audio device
       product: RV620 Audio device [Radeon HD 34xx Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

### Post by markbuntu on 2008-12-02
Is there a switch for it in the Volume Control? 
Right click on the little speaker and choose Open Volume Control 
You made need to make make this switch visible in Preferences.

---

### Post by atomizer on 2008-12-03
nope, no switch.

I selected all options in preferences, and nothing there that switches my subwoofer on.

I think the subwoofer isn't supported yet, but maybe somebody knows a configuration-file I should edit or something like that?

---

### Post by Irishka on 2008-12-03
> **atomizer said:**
> nope, no switch.

I selected all options in preferences, and nothing there that switches my subwoofer on.

I think the subwoofer isn't supported yet, but maybe somebody knows a configuration-file I should edit or something like that?
Subwoofer? Why do you need it on you laptop? Only if you add chrome plated rims and play rap on it ;)

---

