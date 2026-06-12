---
title: "Sound problems still not fixed in 9.04"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by sarasotab on 2009-05-22
Many people have this problem, and I have read most of the threads. But, nothing I have tried works.  Setting the options properly in the Alsa database seems to be the most common fix suggestd

I have tried four or five suggestions for editing the alsa database and none of them have worked. In line three of the suggested options, what does model= refer to. I have an HP 6735s which has the Intel HDA sound card from Analog Devices - AD1984A which in the alsa hardware listing calls for the default settings in the .conf file. The default didn’t work and neither has any of the suggested options. No sound in 9.04 or 8.10. Any help would be greatly appreciated.

Current options (in addition to defaults) in alsa database are:

options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

---

