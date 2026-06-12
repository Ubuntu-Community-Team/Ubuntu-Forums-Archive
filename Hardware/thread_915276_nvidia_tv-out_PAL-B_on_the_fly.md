---
title: "nvidia tv-out PAL-B on the fly"
date: 2008-09-09
forum: Hardware
---

### Post by palomar on 2008-09-09
Hi,
By default I want to use single screen configuration. With nvidia-settings (not as root) I can enable tv-out. But, it's in NTSC format, resulting in black/white colors. 

When running nvidia-settings as root, enable tv-out, save to Xorg file the xorg.conf will be modified. When I manually add 

Option         "TVStandard" "PAL-B"
   
to the Device section, I'll see full color on my tv. 

But I don't want the tv-out to be enabled all the time. When disabling it whit sudo nvidia-settings the PAL-B line will be deleted and when enabling tv-out again using nvidia-settings as local user I get black/white colors again (ntsc). 

So my question is: how to enable tv-out on the fly with PAL standard?

---

### Post by palomar on 2008-09-17
BUMP ^^^^

I also found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151771](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151771) which describes my problem exactly.

---

