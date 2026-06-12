---
title: "Acer Aspire 5739G/nvidia G210M: Screen distorted after standby or switch to VT"
date: 2009-12-23
forum: Hardware
---

### Post by pkerling on 2009-12-23
Hey,

every time I switch to the linux console or resume after suspend, the screen on my acer Aspire 5739G with a NVIDIA G210M graphics card becomes very distorted until I reboot. See [here]("http://img690.imageshack.us/img690/5985/bild0047.jpg"), [here]("http://img38.imageshack.us/img38/9082/bild0050r.jpg") and [here]("http://img697.imageshack.us/img697/51/bild0051.jpg") for an impression of how it looks like. I have already tried disabling intel_agp and setting NvAGP to 1 in xorg.conf, but that didn't change anything. Any ideas? If it matters, Option "ModeValidation" "NoTotalSizeCheck" is set in the xorg.conf Monitor section, because otherwise the nvidia driver will give me only a very limited resolution (mentioned in some other thread).

Regards,
Philipp

---

### Post by cajual on 2009-12-23
Why not use the search feature?

[http://ubuntuforums.org/showthread.php?t=1359721](http://ubuntuforums.org/showthread.php?t=1359721)

---

### Post by sleepee on 2009-12-23
im having the same problem and was thinking of posting pics of it to be able to describe it better (at least better than just describing it as "fuzzy, flickering graphics")..
but good thing you beat me to it.. my digi cam doesn't compare to yours..

---

### Post by pkerling on 2009-12-24
> **cajual said:**
> Why not use the search feature?

[http://ubuntuforums.org/showthread.php?t=1359721](http://ubuntuforums.org/showthread.php?t=1359721)

I did search for quite some time, but every now and then you just miss something :) 

@sleepee: You should also register yourself as affected on the LP bug ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456)) in case you haven't already.

---

