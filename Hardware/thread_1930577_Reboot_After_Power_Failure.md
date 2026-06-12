---
title: "Reboot After Power Failure"
date: 2012-02-23
forum: Hardware
---

### Post by bluehz on 2012-02-23
I am currently running Ubuntu 11.04 as a headless server on an HP d325 CPU.

In previous versions of Ubuntu - if there was a power failure - the machine would reboot itself after the power was restored. This no longer functions in Ubuntu 11.0.4.

Does anyone know how to restore the REBOOT AFTER POWER FAILURE function?

---

### Post by ahallubuntu on 2012-02-23
Ubuntu (or any operating system) has no control over how to handle a power loss.  Instead, you need to set this option in your BIOS Setup: what to do in case of power loss?  Generally you have choices like: leave power off, power up, or previous state (if power was on when power was lost, power back up when it comes back on).

You should get a UPS (battery backup) for any server you care about.  You risk a data corruption if power is lost unexpectedly; a UPS can avoid that.  You can connect up the UPS to your server via USB cable so the server can tell if the battery is about to die - then the server can shut down gracefully before power is completely gone and avoid corruption problems.

---

### Post by bluehz on 2012-02-24
Thx - I thought that would be the case but I never changed the BIOS and it worked previous to Ubuntu 11.x.

---

