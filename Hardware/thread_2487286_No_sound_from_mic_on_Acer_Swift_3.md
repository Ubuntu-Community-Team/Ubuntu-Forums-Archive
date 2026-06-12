---
title: "No sound from mic on Acer Swift 3"
date: 2023-05-29
forum: Hardware
---

### Post by zhelenskiy on 2023-05-29
I recently updated the kernel to 5.15.0-72-generic and my mic stopped working.
I tried to figure out the problem and fix it but failed.
output of `cat /proc/asound/card*/codec* | grep Codec` is```

Codec: Realtek ALC256
Codec: Intel Kabylake HDMI

```

The content of /etc/modprobe.d/snd-hda-intel.conf is:
options snd-hda-intel model=auto

I tried to find the correct model in [https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html](https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html) but failed.

Sorry if I do something wrong. I am new here, it is my first message in the forum.

---

