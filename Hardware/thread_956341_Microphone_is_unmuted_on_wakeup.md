---
title: "Microphone is unmuted on wakeup"
date: 2008-10-23
forum: Hardware
---

### Post by arheon on 2008-10-23
Hi all =)
So... Machine is Lenovo 3000 N200 running Intrepid 8.10b... Everything runs smooth,but mic.After suspend\hibernate > resume I have mic unmuted,causing loud whistle noise which is sound,looping itself through speakers back to mic, to speakers again mic... 
I've muted it in alsa mixer but that doesn't help.
The bug exists [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198839"),but is wishlisted.Well,it's nice but I must mention that it's very annoying.
Danie T Chen [says]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198839/comments/5") : 
> the following entry needs to be added to patch_realtek.c::alc861vd_cfg_tbl[]:

SND_PCI_QUIRK(0x17aa, 0x1867, "Lenovo 3000 N200", ALC861VD_LENOVO),

but I have no idea where does that "patch_realtek.c" sit... Could anybody help me with this issue,please?

---

### Post by arheon on 2008-10-23
up

---

