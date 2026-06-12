---
title: "Nvidia GTX 660ti HDMI blurry"
date: 2013-06-06
forum: Hardware
---

### Post by tOmoness on 2013-06-06
Hey guys,

On my Windows 7 partition I was able to edit the registry to not include the extension block for the EDID info meaning my image became crystal clear, but I'm having trouble trying to find a way to do this in Ubuntu.

Has anyone else experienced this?


Regards,
- T

---

### Post by CatKiller on 2013-06-07
IgnoreEDID used to be an xorg.conf option - it probably still is, but it's not something I've tried for a while. You might also need to manually configure the resolutions/timings that you're after.

---

