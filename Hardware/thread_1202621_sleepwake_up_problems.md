---
title: "sleep/wake up problems"
date: 2009-07-02
forum: Hardware
---

### Post by csab on 2009-07-02
Hi,

I have desktop with ATI HD 2600 Pro video card and using the proprietary driver <fglrx>. With this driver I have had some intermittent problems, one of them is failure to wake up from sleep. The computer hard freezes on me, and I get garbled or black screen.

Experimenting a little I found that if I use pm-suspend directly, then it always wakes up with no problem. This is really strange, because looking at the "hal-system-power-suspend-linux" script, it looks like gnome-power-manager does the very same thing. So what else does it do that may cause the problem? Or how can I stop it from doing those things?

I'm not afraid or reading lots of technical documentation, but I found virtually no deep descrption about how gnome.power-manager works.

---

