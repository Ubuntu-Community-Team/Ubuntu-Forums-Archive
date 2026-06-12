---
title: "how to fix no sound in Karmic 9.10"
date: 2009-11-30
forum: Hardware
---

### Post by sam1948 on 2009-11-30
this is what solved my problem
open shell:
```
sudo aptitude reinstall alsa-base alsa-utils
```
enter password,press enter, let it finish and then:
```
sudo aptitude reinstall alsa-base alsa-utils
```
that's all
enjoy

my hardware : 
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

---

