---
title: "usb keyboard extra function buttons not working"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by mlho on 2008-03-09
Can't quite work this one out.

My old laptop is a Toshiba Satellite 3000 running Ubuntu 6.10 LTS.

I have a USB keyboard with 'extra' buttons. These map fine using kernel version 2.6.15-28, so volume dial works okay as does all the other extra keys (so calculator launches calculator, etc.).

With kernel version 2.6.15-29 and 2.6.15-51, the standard keys work normally, but the extra buttons stop working and result in abnormal mouse behaviour.

So, moving the volume dial instead of changing the volume, makes the mouse behave as it someone had left-clicked and moved the mouse to the right. Other buttons causes similarly bizarre mouse behaviour even though the mouse itself stationary (same behaviour even with USB mouse is disconnected).

Not sure what has changed between the kernel versions.

Tried using xev to work out what was being interpreted by the computer, but it doesn't seem to make much sense.

Mark

---

