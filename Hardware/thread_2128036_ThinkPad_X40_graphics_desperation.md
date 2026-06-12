---
title: "ThinkPad X40 graphics desperation"
date: 2013-03-21
forum: Hardware
---

### Post by oktology on 2013-03-21
I'm at the end of my rope. I cannot get the drivers for the Intel GPU in my ThinkPad X40 working to save my life.

I tried the Glasen PPA Intel drivers on Oneirc with 3.0.0-12, 3.0.0-32, 3.2.40, and 3.3.7 kernels.
I tried updating to 12.04 LTS and installing the Intel open source drivers from Intel.
I've tried forcing the use of the intel driver in my xorg.conf.
I've tried wiping the disk and re-installing fresh.

The worst part is that at one point, right after I first installed 11.10 on this machine, I had it all working. System Settings reported an Intel GM graphics adapter, Compiz ran with all effects. So I know the GPU works, and that Compiz can run on this machine. Not sure what I did to break it, and I cannot figure out what combination of drivers, moon phase, and virgin sacrifices will get me back to that point.

HALP

---

### Post by Yellow Pasque on 2013-03-22
> I tried updating to 12.04 LTS and installing the Intel open source drivers from Intel.
This isn't Windows, so you shouldn't need to install different drivers as the correct drivers for Intel GPU's are loaded/pre-installed by default. If they're not working when you upgraded, then something you did when you were running 11.10 probably borked them.

Post your /var/log/Xorg.0.log

---

### Post by ManamiVixen on 2013-03-22
Also, the drivers from Intel are only for Intel chips older than the i915. So you don't need them unless you have an i865G chipset as an example.

---

