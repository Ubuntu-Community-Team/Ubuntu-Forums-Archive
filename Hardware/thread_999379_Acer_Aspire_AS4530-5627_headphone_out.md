---
title: "Acer Aspire AS4530-5627 headphone out"
date: 2008-12-01
forum: Hardware
---

### Post by yoasif on 2008-12-01
Hey guys... just picked up this laptop, and it works fine, but I've run into an issue that is annoying enough for me to switch into Windows.

The sound from the speakers works fine, but plugging in headphones does not route the audio to the headphone jack. Starting with the headphones plugged in (as has been suggested in other threads) doesn't help either. 

Any help would be appreciated, and I will try to provide whatever information you need that may be helpful. 

Running Ibex here, fresh install.

---

### Post by MonkeyPushButton on 2009-04-24
I had the same issue (again Acer Aspire) and fixed it by editing \etc\modprobe.d\alsa-base.conf adding the following line

```

options snd-hda-intel model=acer

```

the following link helped a ***lot***.

[http://ubuntuforums.org/showthread.php?t=302543&page=2](http://ubuntuforums.org/showthread.php?t=302543&page=2)

Hope this helps.

---

