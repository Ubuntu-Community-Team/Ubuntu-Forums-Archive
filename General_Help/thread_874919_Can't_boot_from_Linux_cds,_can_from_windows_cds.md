---
title: "Can't boot from Linux cds, can from windows cds"
date: 2008-07-30
forum: General Help
---

### Post by mike.f1 on 2008-07-30
I have an older single board computer (mid 90s bios) and can boot from windows cds but can't boot from any linux cd I have tried, including ubuntu, knoppix, and dsl.  I want to run this system from ubuntu without any floppy or hard drive.  The bios cannot be reflashed.  I assume the boot loader on windows cd is different than that normally used in linux.  All cds can be accessed on the system after bootup so the drive is not the problem. (I have tried several different drives.)

Please help

Thanks

---

### Post by Taxman415a on 2008-07-30
Can you tell us exactly what happens when you try to boot with the Ubuntu CD? Be very specific and in addition, copy down the specific errors if you can. I can't remember the commands off the top of my head to get more verbose messages when booting, but they can be looked up if needed. First we need details.

---

### Post by prshah on 2008-07-30
> **mike.f1 said:**
> I have an older single board computer (mid 90s bios) and can boot from windows cds but can't boot from any linux cd I have tried, including ubuntu, knoppix, and dsl.

There is no specific change in the boot loader, as you imagine.

I'd suggest burning the CDs at a lower speed; what is the max speed of the drive you have in this (old) computer? Try burning the CD at 50%~75% of the max speed on the old drive. Eg, if the old drive is an 16x, burn your linux CD at 8x or 12x.

---

