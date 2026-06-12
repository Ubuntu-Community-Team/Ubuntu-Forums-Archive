---
title: "TOLUD and Grub"
date: 2010-04-17
forum: Hardware
---

### Post by replica2010 on 2010-04-17
I have a weird 'issue', which I'm curious about the solution to, just for piece of mind.

System specs is proprietary board (internal, confidential, validation) with an intel 975x chipset, core 2 duo, and 4gb memory.  The bios has many fun options (if anyone happens to have a breakdown of what half the SV stuff means, I'd be very grateful...).  One of the options is Top Of Low Usable DRAM, which seems to be pretty standard.  If I set this to 3.25gb, grub stops "working": It either displays nothing (blank screen), or some screwed up wackiness (I can't explain better; sort of an acid trip combined with a defrag display? you know, hosed) or it'll show the grub menu, but keys have no effect (ie, hitting enter, or 'c', or 'e').  Timeout is set to 5 seconds.

The system BOOTS, after the delay, IF I don't hit esc, etc, to get to the menu.  So, this isn't a must fix issue, because when I need to boot to my console runlevel, I can change the bios setting TOLUD back to 2.75gb or under (2.50, 2.25, 2.00, 1.75 and 1.50gb being the other options), and everything's peachy. Memory Reclaim set at auto works regardless of the TOLUD setting. If TOLUD is set to 3.0gb or 3.25gb, though, results as above.

Does anyone know of a fix to this, or has anyone even heard of this sort of thing, or have any guess what might be going on? I realize that what should be happening (?) is that the PCI MMIO should be 'behind' the 4gb, but why is 2.75gb (and under) magic for grub?

---

