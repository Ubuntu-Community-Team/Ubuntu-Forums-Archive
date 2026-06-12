---
title: "[ALSA]Headphone jack not working - HP Pavilion dv7"
date: 2016-05-18
forum: Hardware
---

### Post by Morgan_OBrien on 2016-05-18
Hello, I have an HP Pavilion dv7 now running Ubuntu 16.04 LTS. After a recent update (not to 16.04, maybe the one before?), the headphone jack no longer works. The onboard speakers still work, and play audio even when the headphones are plugged in. I've tried all controls maxed / unmuted in various configurations in alsamixer. Output of [alsa-info.sh]("http://www.alsa-project.org/db/?f=f3bceb8783257dbfd36fb217864d948d19ff7797"). Tried adding a couple lines to /etc/modprobe.d/alsa-base.conf:

```
options snd_hda_intel model=hp_dv5
options snd_hda_intel enable_msi=1
```

Any help is appreciated.

---

