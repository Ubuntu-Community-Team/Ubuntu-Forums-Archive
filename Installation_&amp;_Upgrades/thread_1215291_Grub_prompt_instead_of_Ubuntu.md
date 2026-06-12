---
title: "Grub prompt instead of Ubuntu?"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by Doggonit on 2009-07-17
So, I installed Ubuntu 9.04 as follows on a 120GB hard drive:

/ -> 20GB, Primary
/home -> 30GB, Primary
swap -> 2GB, Logical
/data -> 68GB, Logical

However, after formatting, partitioning, and installation finished, and the computer rebooted and asked me to remove to CD (which I did), I only got a grub prompt and I haven't a clue how to use that piece of garbage and why Ubuntu won't boot.

When I selected to add a boot loader (so that I might eventually install Windows or whatever else on one of the two empty 40GB hard drives also in the rig), I left the location as the default one, i.e.: hd0

Trying to reinstall everything and putting the bootloader in hda5, where / is, didn't do a damn either.

What do I do to get this rubbish working?

---

### Post by merlinus on 2009-07-17
You might try this at the grub prompt:

```
root (hd0,0)
setup (hd0)
quit
```

and restart.

This assumes that / is the first partition on the hdd you are booting from.

---

### Post by Doggonit on 2009-07-17
I get the following for bot root (hd0,0) and (hd0): 
Error 22: No such partition

On the BIOS level, I don't see the 120GB hard drive, just the two 40GB ones and the DVD and CDRW drives. And it's also the same at the Power-on Self Test.

Could it be that as the 120GB HDD is attached to a PCI IDE card, it can't be booted from?

---

### Post by merlinus on 2009-07-17
What happens if you disconnect the two 40G drives?

---

### Post by Doggonit on 2009-07-17
Hm, I get a:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

I suppose that whilst the IDE controller card (PCI) works fine as Ubuntu was successfully installed (I can see that much when using the CD as a Live CD) there, it cannot boot from that, so I'll just rearrange the cables and try again.

---

### Post by Doggonit on 2009-07-17
It's alive! :D

Lesson is: Don't have 3 optical media drives and 3 hard drives in an old rig running an extra PCI IDE controller because you only have two IDE connections (so two master/slave pairs) to the motherboard. Your linux drive may be one of the ones hooked up to the PCI IDE controller, and thus will NOT boot until reconnected directly to the motherboard.

---

### Post by merlinus on 2009-07-17
Excellent, and you learned quite a bit into the bargain!  Have fun, and post back should you run into other difficulties.

---

