---
title: "noise during first stages of boot"
date: 2011-12-27
forum: Hardware
---

### Post by sanderd17 on 2011-12-27
hi, 

when I boot my desktop, it's making a loud noise during the first stages of the boot(probably the POST). 

It's a noise like a fan that isn't running smoothly, or a HDD with serious problems. But when GRUB appears, the noise becomes more silent, when gdm is loaded the noise is completely gone, and I never hear it again, not even under heavy io or cpu/gpu load. The noise is typical for a skinning

Does anyone know what could be producing such a noise during the POST? I would like to have an idea before I open the case.

Thanks

---

### Post by QIII on 2011-12-27
I'd say you need to positively identify the component making the noise instead of thinking what it *could* be. It *could* be many things and making speculative stabs at what it is would be a waste of your time.

Diagnose, you know.

A lot of things that spin up during the POST could be the trouble.  The fans spin up just because they are now powered.  Your CPU HSF spins up.  The BIOS is looking for all your hardware to do the POST and it spins up your disks and DVD player.

Once spun up, there may not be noise.

If you sleep or hibernate and then wake it up after a few minutes, does it do the same?

---

### Post by sanderd17 on 2011-12-27
> **QIII said:**
> I'd say you need to positively identify the component making the noise instead of thinking what it *could* be. It *could* be many things and making speculative stabs at what it is would be a waste of your time.

Diagnose, you know.

A lot of things that spin up during the POST could be the trouble.  The fans spin up just because they are now powered.  Your CPU HSF spins up.  The BIOS is looking for all your hardware to do the POST and it spins up your disks and DVD player.

Once spun up, there may not be noise.

If you sleep or hibernate and then wake it up after a few minutes, does it do the same?

It didn't make noise when comming out of sleep, I didn't try from hibernate.

I tried to diagnose it, and when I booted the computer with the case open, there was no noise. I closed the case again, and every thing is OK. 

I still don't know what was wrong, but at least it's solved. Thanks for helping.

---

