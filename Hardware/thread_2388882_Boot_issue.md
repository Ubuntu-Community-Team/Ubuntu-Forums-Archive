---
title: "Boot issue"
date: 2018-04-08
forum: Hardware
---

### Post by standy2 on 2018-04-08
Not sure if I have just lost my hard disk or not..  system has been working fine for months till I got core dump message and now

getting following error on boot..
 no such device 5fc........c.
unknown filesystem
Entering rescue mode...
grub rescue>


ran disk tests from the live CD and everything tested OK
use the boot repair tool result..   [http://paste.ubuntu.com/p/gbbRbcc4pv/](http://paste.ubuntu.com/p/gbbRbcc4pv/)  and I probably need someone with more experience to diagnose its result

just trying to gauge whether need to start again (reinstall) / replace Hard disk or persist with trying to repair

any help appreciated

---

### Post by oldfred on 2018-04-08
You are only showing Windows on sda1, but no sdb drive at all.

Does BIOS show the second drive?
If not seen by BIOS, it cannot be then seen by operating system.
And then check connections and possibly replace cables.

---

