---
title: "Ubuntu 10.10 Alienware m9750 Audio problems"
date: 2011-01-06
forum: Hardware
---

### Post by rooneybuk on 2011-01-06
Hi All,

There have been various post about this in the past but it seem it has returned again with the new release of 10.10 and with no easy fix.

I have tried adding both the following module option and neither work

Using
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

This just gave speaker audio and no headphone audio
```
options snd-hda-intel model=6stack-dig
```

This just gave speaker audio and no headphone audio
```
options snd-hda-intel model=arima
```

With nothing defineded e.g. default i get sound from both which it should just be headphone if there connected.

Please Help

#new info#

It appear I can unmute the headphones in alas mixer but when the system restarts it revert back to being muted, even when I use alsactl store.

---

