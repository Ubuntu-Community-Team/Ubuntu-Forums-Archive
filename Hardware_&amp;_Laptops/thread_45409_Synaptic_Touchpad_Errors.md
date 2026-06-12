---
title: "Synaptic Touchpad Errors"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by ecliptik on 2005-06-30
I've been using Hoary for the last few weeks and I've never had performence problems until the last couple days. For some reason my touchpad will "stick" and it looks like the machine studders some. This is what's showing up in my /var/log/messages:

```

Jun 29 21:51:00 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Jun 29 21:51:00 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Jun 29 21:51:00 localhost last message repeated 4 times
Jun 29 21:51:00 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.

```

The only thing I can think of that changed is some new kernel updates that came through the normal ubuntu respositories. It also seems to affect DVD playback since it sticks the entire machine. Anyone have any ideas? Or do I have to wait for a new kernel or roll my own? Thanks.

---

### Post by elsewhere on 2005-07-01
If you're running powernowd, try disabling it and see if that helps.  CPU scaling on some kernel/system combinations causes that hiccup, my own included.

Hope this helps...

Cheers,
KV

---

### Post by ecliptik on 2005-07-01
ah, that's probably it, I just updated the bios and all my power stuff like cpu scaling started to work, so I'll disable it and see if it helps, thanks.

---

