---
title: "Screen tearing with NVIDIA on Thinkpad T420"
date: 2016-12-19
forum: Hardware
---

### Post by nessossin on 2016-12-19
I recently purchased a Lenovo Thinkpad T420 laptop and decided to install Ubuntu on it. Everything went smooth, installation was fine, but when I installed nvidia-367 driver so I can use my Nvidia card, and then enabled it, I get screen tearing when I scroll pages, watch videos. When I change to Intel card in Nvidia X Server Settings, it works, no tearing. I can continue using intel card but it would be nice if I could get Nvidia to work.

So far I have tried changing /etc/X11/xorg.conf, putting the following code into nvidia device section:

```
Option         "metamodes" "nvidia-auto-select +0+0{ ForceFullCompositionPipeline = On }"
```

I have also tried putting Nvidia on High Performance in Nvidia X Server Settings.

If anyone could help me, I would really appreciate it.

---

