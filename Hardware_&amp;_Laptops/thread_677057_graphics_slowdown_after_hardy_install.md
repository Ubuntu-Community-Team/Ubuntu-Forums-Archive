---
title: "graphics slowdown after hardy install"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by yingjai on 2008-01-24
Under Gutsy, my laptop was running smoothly. After I installed Hardy (in an attempt to fix my suspend/hibernate issue because someone said it helped), my laptop started to lag. I have some Compiz effects turned on, but it was fine before.

```
dmesg | grep agp
```
returned with something like Detected 8060K stolen memory.

Is there a way to set the amount of video ram? I have an Intel 855GM chipset and no, the setting is not in the bios. My bios is very bare. The only setting memory related is the memory performance mode.

I tried dpkg-reconfigure xserver-xorg, but in Hardy, it no longer allows you to set the video ram size.

Even after all this trouble, my suspend and hibernate is still broken....

---

