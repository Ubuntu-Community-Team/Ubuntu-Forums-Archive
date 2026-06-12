---
title: "Gateway Laptop Brightness"
date: 2009-11-02
forum: Hardware
---

### Post by Vitamin_A on 2009-11-02
Hi all,

I've recently updated to Ubuntu 9.10 from 8.10 (via 9.04), and I've noticed one thing.  I used to have the brightness working by invoking the "xrandr --output LVDS --set BACKLIGHT_CONTROL native" at startup, however, this command does not seem to work anymore, and thus, I have no more control over the brightness of my computer.  Is there a fix for this?

The output error message that I get is:
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26


Thanks.

EDIT:  Thought it might be useful to know, that this problem doesn't appear on older kernels that I have listed in my GRUB (2.6.28-16 and 2.6.27-15), but only on 2.6.31-14.

---

### Post by craigrouse on 2009-11-04
Hi. I don't have a fix yet, but I get the exact same problem on a Gateway M6829b laptop. This is a regression since Jaunty. I will file a bug report when I get the time, but in the meantime any ideas would be appreciated! Thanks.

---

