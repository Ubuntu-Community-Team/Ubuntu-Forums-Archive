---
title: "VGA fan runs constantly with dual head"
date: 2009-11-13
forum: Hardware
---

### Post by arch0njw on 2009-11-13
I have a dream... a dream of two monitors and a VGA fan that doesn't run all the time.

This is my GPU from an "lspci" output: ```
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
```I have (1) a 21" SyncMaster 204B and (2) a 23" HP 2509m.  When I connect one-or-the-other, my VGA is fine.  When I dual-head them through either TwinView or directly editing the xorg.conf the VGA fan starts running and doesn't stop.

I first connected these such that one monitor was hooked up by DSUB/VGA and the other by DVI.  I plan to try both being hooked up by DSUB to see if it makes a difference.  I don't know why it would, but I'll try.


Is the fan running normal behavior?  Would a more powerful card not have the fan run?  I'd love some help here to sort this out.

---

### Post by arch0njw on 2009-11-25
I posted something over in the EVGA forums -- they're the manufacturer of this card.
[http://www.evga.com/forums/tm.aspx?high=&m=40959](http://www.evga.com/forums/tm.aspx?high=&m=40959)

As clarification, on a normal day the fan runs.  However, if I run both monitors, the fan seems to run at max RPM.  That's what's bugging me.  Right now, with one monitor, the fan is running normally and is not loud.  If I start something with intense graphics, the fan will kick up to max RPM -- I kind of expect that.  But I don't expect that with dual head.  Is dual head really that intensive?

---

### Post by arch0njw on 2009-11-27
I finally got around to trying this with two dsub/vga adapters on the DVI ports.  For whatever reason, it is not causing my fan to run.  I finally found "nvclock" and am using that to monitor performance.  The changes are not much, and the GPU fan has not yet kicked up to run any harder.

< startup (with one monitor)
> after running for 15 minutes with two monitors

< GPU clock:    468.000 MHz
---
> GPU clock:    518.400 MHz
17c17
< Clock:                661.500 MHz
---
> Clock:                688.500 MHz
25c25
< GPU temperature: 43C
---
> GPU temperature: 55C

Unless things change radically, I think this solved my issue.

---

