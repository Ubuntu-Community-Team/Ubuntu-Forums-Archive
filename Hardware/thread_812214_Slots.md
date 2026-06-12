---
title: "Slots"
date: 2008-05-29
forum: Hardware
---

### Post by SolaceAvatar on 2008-05-29
Alright, I'm getting a laptop with an internal hard drive an external SD slot. I've heard that SD slots are basically the same as SDD's except you can, you know, remove the SD cards, and since SDD's have some advantages over hard drives, I'd potentially like to keep an SD card in there permanently and boot off it. So, a few questions:

1. Is that essentially accurate and doable, and are there any disadvantages to doing that versus using an internal SDD?

2. If I keep the OS(s) and (most) programs on the SD card, can/does the hard drive turn off when it's not being used?

3. Kind of an aside, but it also comes with an Express Card/54 slot, and... what is that and what is it used for?

---

### Post by sgt.sargent on 2008-05-29
> **SolaceAvatar said:**
> Alright, I'm getting a laptop with an internal hard drive an external SD slot. I've heard that SD slots are basically the same as SDD's except you can, you know, remove the SD cards, and since SDD's have some advantages over hard drives, I'd potentially like to keep an SD card in there permanently and boot off it. So, a few questions:

1. Is that essentially accurate and doable, and are there any disadvantages to doing that versus using an internal SDD?
Your SD slot may not be bootable (depends on the BIOS) and if its just SD (not SDHC) it'll only go up to 2 Gig (SDHC is likely if the slot is newer hardware, but not if they slapped in a slot design they've had laying around a while).

> **SolaceAvatar said:**
> 2. If I keep the OS(s) and (most) programs on the SD card, can/does the hard drive turn off when it's not being used?Turn off as in stop? That again depends on the hardware, though also the software's support for interfacing with the hardware's power savings modes.  The hardware on a notebook will likely have low power modes, but getting the kernel modules (drivers, etc.) set up to use the power savings modes on the hardware may be a bit of work and that's assuming that they exist for that hardware.

> **SolaceAvatar said:**
> 3. Kind of an aside, but it also comes with an Express Card/54 slot, and... what is that and what is it used for?Express Card is a replacement for the old PCMCIA cards.  54 is the bigger sized form factor.  Cards use either PCI Express or USB 2.0 and can in theory be pretty much anything anyone can squeeze in to the form factor.  This may be another option for you as their are Express Card drives, so (depending on BIOS) you might be able to boot from that slot instead.

---

### Post by SolaceAvatar on 2008-05-29
Ah, that's good to know. I'll dig around when it actually arrives (should be tomorrow), but on the site it just says SD so I'm glad I didn't buy one of those SDHC cards. As far as any three of those goes, if I can boot off it it's pretty much the same as an SSD, right?

---

### Post by sgt.sargent on 2008-05-30
If you can boot from it, whether its old style SD, SDHC, or Express Card, it should act like a drive, yes.  Express Cards, especially PCI (as opposed to USB) cards would likely give you better performance though.

---

