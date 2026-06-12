---
title: "[SOLVED] Why xorg-server-intel?"
date: 2008-10-30
forum: General Help
---

### Post by GuiGuy on 2008-10-30
one of my  Mythbuntu frontends, which is AMD AM2/ nvidia 7200GS based, this morning lists "xorg-server-intel" as an available update.

As I recall, the last time this thing was included in an update it wreaked havoc. I became so annoyed and frustrated at being unable to sort it out that I reinstalled/ reconfigured the frontend from a backup image. 

So this time, can someone advise me if xorg-server-intel is an essential part of the OS and should it be updated?

Thanks

---

### Post by Yellow Pasque on 2008-10-30
If you mean xserver-xorg-video-intel, it can safely be removed through Synaptic if you're not using Intel integrated graphics.

If you weren't using the intel video driver, then updating it wouldn't have any effect on your system. It must have been something else in that batch of updates.

---

### Post by GuiGuy on 2008-10-30
> **Temüjin said:**
> If you mean xserver-xorg-video-intel, it can safely be removed through Synaptic if you're not using Intel integrated graphics.

Thanks, and yes it is xserver-xorg-video-intel. My typo :(. 

I'll remove it and see what happens :)

---

### Post by GuiGuy on 2008-10-30
> **GuiGuy said:**
> 
I'll remove it and see what happens :)

No ill side-effects

Cheers

---

