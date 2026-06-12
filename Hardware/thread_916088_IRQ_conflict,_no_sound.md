---
title: "IRQ conflict, no sound"
date: 2008-09-10
forum: Hardware
---

### Post by clinto on 2008-09-10
After I upgraded my machine, my integrated sound mysteriously stopped working.  I was in Windows at first, so I started tinkering with my driver and cause Windows to hang at boot(imagine that).

I booted into linux and no sound.  So I checked my POST and sure enough the sata/raid card I'd installed was on the same address as my "multimedia device," being my onboard sound.

I couldn't figure out how to change my IRQ settings, so I pulled the card and reset my BIOS.  However, still no sound.

I don't understand why anyone would write CMOS without giving a user the ability to manually change IRQ addresses.  Am I missing something?  The only thing I came across was:
PnP/PCI Configuration > IRQ Resources

It shows IRQ3 through IRQ15(excluding 13), but only allows me to toggle them between "PCI Device" and "Reserved."

I was looking and apparently there's a way to change IRQ assignment in Windows.  [http://www.helpwithpcs.com/upgrading/change-irq-settings.htm](http://www.helpwithpcs.com/upgrading/change-irq-settings.htm)  Is this possible in linux as well?

I'm not sure if anyone can help me, save I take pictures of my cmos settings.  If I need to provide any more info, let me know.

---

### Post by DoctorMO on 2008-09-11
Sounds like your computer is a little confused. normally the BIOS allows you to pick and choose what IRQs to use for certain things. Although I take it the onboard sound wasn't disabled in the BIOS as a yes/no option?

---

