---
title: "USB problems"
date: 2010-06-02
forum: Hardware
---

### Post by javyn999 on 2010-06-02
Hey everyone.  I have an old Athlon XP2800+ box here, w/ Abit mobo, 2 gig ram.

A few months ago, the USB seemed like it was going out on the mobo.  

Replacing the motherboard was out, because finding a Socket A with onboard SCSI controller is pretty hard, and the ones I have found cost upwards of a new system entirely, which I cannot afford atm.

The problem I am having is when I plug a usb drive in, it mounts the drive, reads all the files just fine, but when I try to open or transfer large files like video, or even transfer many small files at once, the file manager window hangs, and the drive disappears in my list.  

Resulted in the corruption of many of the files on my external hd. :(

Since the mobo I need is so expensive, I figured I'd just get a Rosewill PCI USB controller off newegg.  Slapped it in, and lo and behold, SAME problem!  

Not an OS issue, I boot Windows XP and Ubuntu off this box, the issue persists in both operating systems.  And the drives work just fine on other computers.

Has anyone experienced any sort of problem like this?  Strangely, my USB mouse is unaffected.

---

### Post by BoneKracker on 2010-06-02
Have you tested the system with other external USB storage devices (such as a USB flash key or a different external USB drive) and found the same behavior?

---

### Post by mindpowerz on 2010-06-03
Could also be due to faulty Southbridge on the motherboard, the chipset handling USB interface management/control.

---

### Post by javyn999 on 2010-06-03
> **BoneKracker said:**
> Have you tested the system with other external USB storage devices (such as a USB flash key or a different external USB drive) and found the same behavior?

Yeah, I have a lot of USB storage drives and all exhibit this behavior, even my cell phone when I plug it in.

> Could also be due to faulty Southbridge on the motherboard, the chipset handling USB interface management/control.

I guess that's it.  I don't know what else it could be since my PCI and Mobo controllers are bunk.  I have also tried two different PCI controllers even, same effect.

---

