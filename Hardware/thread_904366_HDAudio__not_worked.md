---
title: "HDAudio  not worked"
date: 2008-08-29
forum: Hardware
---

### Post by quasitr0n on 2008-08-29
I take canonic kernel without load modules. But doesn't hear any sounds, because my soud-card not worked.
Why occur it's? It's realy using without load modules?
```
# grep HDA .config
NFIG_SND_HDA_INTEL=y
CONFIG_SND_HDA_HWDEP=y
CONFIG_SND_HDA_CODEC_REALTEK=y
CONFIG_SND_HDA_CODEC_ANALOG=y
CONFIG_SND_HDA_CODEC_SIGMATEL=y
CONFIG_SND_HDA_CODEC_VIA=y
CONFIG_SND_HDA_CODEC_ATIHDMI=y
CONFIG_SND_HDA_CODEC_CONEXANT=y
CONFIG_SND_HDA_CODEC_CMEDIA=y
CONFIG_SND_HDA_CODEC_SI3054=y
CONFIG_SND_HDA_GENERIC=y
# CONFIG_SND_HDA_POWER_SAVE is not set
# dmesg | grep HDA
  #0: HDA Intel at 0xf7100000 irq 22
#lspci | grep HD
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

---

### Post by quasitr0n on 2008-08-29
help
up.

---

