---
title: "disk management (lucid)"
date: 2010-05-12
forum: Hardware
---

### Post by chitowner2 on 2010-05-12
Hi folks,

Here's a left-field kinda question: How can I know positively which actual disk is at fault when one fails in a RAID array?

In other words, is there some way to know which port (SATA) the faulty drive is connected to?

It is meaningless in this context to look at "sd*" labels of course. If I had thought about it at the right stage of building the system, I might have made a map of UUID numbers, but I didn't.  I now have a drive which is still spinning, but not digitally active, so without doing a one-at-a-time dissection of my system (nine disks!) I can't tell which is at fault.

Ideas?
CT

---

### Post by MSPdwalt on 2010-05-13
Is there a *nix RAID manager available for your card?  That would be the sure fire way...or check the pre-boot configuration screen.

---

### Post by chitowner2 on 2010-05-22
I am using software RAID with LVM, not hardware RAID.

---

