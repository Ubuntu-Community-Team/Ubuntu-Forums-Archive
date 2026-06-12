---
title: "Strange dark gradient on laptop monitor (ThinkPad X200S)"
date: 2014-07-18
forum: Hardware
---

### Post by markus15 on 2014-07-18
Hi,

I've just installed Ubuntu 14.04 on my old laptop. Everything else is great out of the box, but my laptop screen is super dark, and the regular laptop brightness setup doesn't do any visible change, even though I can see the scrollbar going back and forth. The darkness is almost complete on the left side of the screen, and changes gradually to the right side, where it's readable but still dark. All three external monitors I've tried work fine, it's just the laptop screen. My dual-boot Windows 7 also works fine on the laptop screen.

Any ideas what to do? Thank you in advance for any help.

---

### Post by tgalati4 on 2014-07-18
Perhaps the power-saving is turned on?  Open a terminal:

```
xset -dpms
```

Check the BIOS for power-saving modes.  Turn off any screen-related timeouts.

---

### Post by markus15 on 2014-07-23
This got actually partially fixed without me doing anything, and worked normally the next time I tried! However, the same erroneous behavior has been present at least twice since - just to function again the next time (or after booting). The laptop screen also always opens first in the darkest possible setting. The gradient disappears on the second-darkest setting, displaying an evenly lighted screen on all further steps.

In a nutshell, very strange and random behavior still, but it's ok most of the time, so I won't bother myself with it anymore. Thanks for the help anyway!

---

