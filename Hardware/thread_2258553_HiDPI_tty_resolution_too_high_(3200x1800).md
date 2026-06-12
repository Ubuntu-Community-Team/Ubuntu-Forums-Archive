---
title: "HiDPI tty resolution too high (3200x1800)"
date: 2014-12-28
forum: Hardware
---

### Post by kurt miller on 2014-12-28
On a Samsung Book 9 HiDPI display running 14.10:

Looking for a way to configure the resolution for tty 1-6 etc.  When I switch via alt-ctrl-f1 I'm presented with a unsuable 3200x1800 resolution display making the text so tiny as to be unusable.  

I've tried the grub mod:

GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=keep

But that has no effect.

---

### Post by dpezely on 2015-01-10
The resolution you tried might not be supported natively by the Intel  integrated GPU in your laptop, so run `vbeinfo` from the Grub prompt  before the kernel is booted.

Also, evenly divisible values of QHD+ 3200x1800 may be a safe bet rather than other resolutions.  Consider: 1600x900

Be  sure to add `auto` to end of list, in case of a typo or incompatible  resolution (e.g., in case config gets copied to another machine in  future) which will at least run using defaults.  

GRUB_GFXMODE=1600x900,auto

(Unfortunately, Intel docs and Samsung docs don't provide a list of native resolutions, so vbeinfo is your best and safest bet.)

---

