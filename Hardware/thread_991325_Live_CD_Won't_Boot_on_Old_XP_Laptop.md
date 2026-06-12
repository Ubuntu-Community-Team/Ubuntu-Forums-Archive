---
title: "Live CD Won't Boot on Old XP Laptop"
date: 2008-11-23
forum: Hardware
---

### Post by Universal344 on 2008-11-23
I recently found an old XP laptop that I want to run Ubuntu on.  However the system refuses to boot the live cd and goes directly to booting xp.  This is what I've already tried:

-Setting the BIOS to boot CD ROM / DVD ROM before HDD (still booted XP)

-Running the live cd on another pc and checking it for defects (reported disk completely error free)

-Writing the image to a USB drive using the utility on the live cd (did not work on either the laptop or my main computer)

-Upgrading my BIOS (I could not do this because the manufacturer of the BIOS wanted me to download software that many people reported as a scam)

Does anyone know how to make the system boot the live cd?  It would be preferable if I didn't have to wipe my HDD of all currently existing data.  I suspect I might be able to do it through safer mode with command prompt but I don't know the command.

Thanks for any help you can provide.

---

### Post by Mewshi on 2008-11-23
It is actually possible that boot from CD, despite being set to occur before HDD load, is still disabled; check that.

Also, you *could* try using Wubi, but I've not heard stellar reviews of it, but, hey, what the heck, if nothing else works, it's worth a shot ^_^

---

