---
title: "Grub + fixmbr = dead computer?"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by SaxMeister13 on 2009-05-01
First off...I'm very new to this whole thing, so I apologize in advance if I say anything stupid.

I'm working with XP SP2 and Ubuntu 8.10 since I already had the disc.  Basically, I installed Ubuntu to a separate HDD, couldn't load GRUB, and tried Windows Recovery to see if I could get at least XP functional again.  After running fixmbr, though, neither OS will boot and I can't even get the Ubuntu Live CD to load.  (I'm on a separate computer at the moment.)

I'm freaking out and can barely think straight about it.  So...sorry to ask such a vague question, but...what can I do? :(

---

### Post by Sewje on 2009-05-01
To get your windows to boot again you also need to run:

fixboot c:

if your xp is on drive c:
you should run a diskscan once you get back into xp

---

