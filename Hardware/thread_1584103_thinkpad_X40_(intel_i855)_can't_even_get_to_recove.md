---
title: "thinkpad X40 (intel i855) can't even get to recovery mode"
date: 2010-09-28
forum: Hardware
---

### Post by noamr on 2010-09-28
Hello,

I'm using thinkpad X40, which has i855 graphics card.

I previously managed to boot my system fine with a newer kernel (2.6.34, I think), but then I deleted it, and now the default, updated kernel (2.6.32.something) stops with a blank screen even in the recovery mode, even when I add i915.modeset=1 to the kernel options in grub. I tried a live USB, which freezed just the same, but worked when I added the i915.modeset=1 option.

Is there a way for me to boot the system from the kernel of the live USB, so that I would be able to install another kernel on my hard drive?

Thanks a lot,
Noam

---

