---
title: "Random Freezing"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by spetroff on 2009-09-12
I am at a bit of a loss in figuring out why my system randomly freezes. It's a fresh ubuntu studio install (9.04) utilizing a simple 3 partition software raid 1 setup. (sometimes the install goes fine other times it does not...) WipeDrive reports no errors when it writes to every sector of the hard drives, Memtest reports no errors after a 3 hour run, and in it's previous life as a Windows box, there were no issues with heat or any other hardware problems. The system hangs on seemingly random tasks (installing software, changing preferences, launching applications). How can I get a hold of some kind of error messaging to help me diagnose this? Thanks

Shane

---

### Post by intrader on 2009-10-01
Similar problem here with various mouse actions. Hangs and have to unplug and reboot. I suspect that the problems lies with the animation software that I have turned on (don't remember where)

---

### Post by earthpigg on 2009-10-01
spetroff: may be bad RAM. consider giving this tool a shot: [http://www.memtest86.com/](http://www.memtest86.com/) .... may need to let it run overnight. it tests very thoroughly. low level operating-system-neutral tool.

intrader: to verify your suspicion, try turning the animation software off and see if that fixes it.

---

### Post by ronparent on 2009-10-01
You might also try running the live cd by changing the boot options by X'ing out the apic, lapic options prior to booting from the cd. If it runs for some time with no freezes then you can either install with those functions disabled or add the noapic, nolapic option to the grub boot line. This fixed the problem for me on three boxes that wouldn't run 9.04 otherwise! That said, there are other causes also.

---

