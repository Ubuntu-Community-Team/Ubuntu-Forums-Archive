---
title: "Intel Z8350 ALSA sound problem rt5651"
date: 2017-12-12
forum: Hardware
---

### Post by daniel-latanie on 2017-12-12
There is no sound on ubuntu, alsa-info during tests shows:

cat: '/sys/module/snd_soc_sst_bytcr_rt5651/parameters/*': No such file or directory

But this one exists:
/sys/module/snd_soc_sst_bytcr_rt5651/

There is just no "parameters" subdirectory.

Here is entire alsa-info dump log:
[http://www.alsa-project.org/db/?f=ce76ee4bcbe44180c822bdd61f4993dd2495508d](http://www.alsa-project.org/db/?f=ce76ee4bcbe44180c822bdd61f4993dd2495508d)

---

