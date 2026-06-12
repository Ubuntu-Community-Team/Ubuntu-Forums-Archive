---
title: "Mouse freeze after a couple of minutes"
date: 2008-08-30
forum: General Help
---

### Post by spylt on 2008-08-30
Hi everybody,

I installed Hardy Heron a few days ago (my first steps with Linux). A couple of minutes after I logon, my mouse freezes. Always.

I tried several things, all with negative result:
- My standard mouse is USB/wireless/optical. So I tried another mouse (USB/optical). I tried the mouses on another USB port.
- I tried the Ubuntu protected mode, and recovery mode.
- I used "noapic" and "acpi=off" (acpi=off does not let me logon - mouse and keyboard are deactivated).
- The freeze happens in all kind of applications. Sometimes 20 seconds after logon, and not later than 20 minutes.
- Alternatively I installed OpenSUSE 11.0, same result.
- I tried the Knoppix 5.3 live system - and that worked as only Linux one. Windows works fine, btw.

Does anybody know how I can solve the problem?
Thomas

---

### Post by nikgare on 2008-08-31
Have you tried a standard PS/2 mouse, or just USB?

---

### Post by spylt on 2008-09-01
I just have USB mouses. I could organize PS/2 from friends or the company I am working for.

---

### Post by pgatrick on 2008-09-01
Do you have an nvidia gfx card? I used to have a problem like that if I had nv installed, only solution for me was the nvidia binary driver. :/ Also my current mobo is crap and does that, but acpi=off works for me, I do have to also use the boot option 'irqpoll' to get everything to work though, don't know if that might help you?

---

### Post by spylt on 2008-09-03
Yes, I have an NVidea graphic card, and I tried with NV and NVidea drivers - both negative.

However, I solved the problem! It seemed to be an IRQ conflict with the graphic card. Disabling the USB legacy support in BIOS helped, and now I flashed the BIOS with the latest version, which also works find (and I don't have to buy a PS/2 keyboard to switch between installations in Grub).

---

