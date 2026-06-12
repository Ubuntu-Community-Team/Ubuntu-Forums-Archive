---
title: "Skylake audio kernel support"
date: 2020-05-12
forum: Hardware
---

### Post by matt-theworldtree on 2020-05-12
For audio to work on Skylake Chromebooks, [COLOR=#24292E][FONT=SFMono-Regular]CONFIG_SND_SOC_INTEL_SKYLAKE[/FONT][/COLOR] needs to be enabled in the kernel config such that the module [COLOR=#24292E][FONT=SFMono-Regular]snd-soc-skl[/FONT][/COLOR] can be loaded. We've put a lot of work into tinkering with this in the GalliumOS forums here: [https://github.com/GalliumOS/galliumos-distro/issues/379](https://github.com/GalliumOS/galliumos-distro/issues/379) . 

Beyond asking for this kernel-level change or setting up a PPA with a modded kernel, is there a different workaround we can pursue? If not, is there a downside to enabling that flag?

---

