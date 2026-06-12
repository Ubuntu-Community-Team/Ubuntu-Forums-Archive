---
title: "Ubuntu 9.04 stuck @ boot."
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by zebala on 2009-08-09
Hi all,

I just installed ubuntu on an older piece of hardware.

AMD Duron 800 mhz
ATI Radeon 9600 SE
768 SDRAM
Maxtor N256 HD

Everything seemed to work fine at first, but the second time after one successful boot it just got stuck at the black screen with a unmoveable mouse cursor. What's weird it sometimes boots, and sometimes not. If I'm lucky, ubuntu will boot 1/5 of the time. I reinstalled ubuntu desktop but I don't know if that helped, since I didn't boot enough times. Also I get an "IO Apic resources could not be allocated" during boot before the splash. When ubuntu finally boots it blinks once or twice weird colours(+static) all over the screen but works fine after that. Could these be linked to the problem? Any ideas?

Thanks in advance.

---

### Post by zebala on 2009-08-09
Well ubuntu has been booting fine for a few times, so this may not be a problem anymore. Still no ideas what's causin the IO APIC issue?

---

### Post by P4man on 2009-08-09
Probably a buggy bios ACPI implementation. Can you flash it to a newer version? Or disable acpi in the bios, although that may result in some loss of functionality when it comes to power management.

Also, if you keep having troubles booting, try adding noapic to your kernel startup parameters; in grub, press "e", select the kernel line, and add "noapic" without quotes at the end. To make that change permanent, edit grub's menu.lst.

---

### Post by zebala on 2009-08-09
Thanks a lot I will try this and see how it goes!

[EDIT] Duh there only seems to be a BIOS version that's from the same year and I doubt it's done much. Especially when here [http://www.biostar-usa.com/mbdownloads.asp?model=m7vka](http://www.biostar-usa.com/mbdownloads.asp?model=m7vka) it says it only fixed those problems. In addition, I don't know if my board vka1031f or vka1031b. It is a fujitsu siemens package deal so the BIOS may be their own version.

---

### Post by zebala on 2009-08-14
Ubuntu still hung on boot, but after adding the "noapic" line in the /boot/grub/menu.lst I haven't had a problem since! The flashing is gone too! Thanks a lot.

---

### Post by presence1960 on 2009-08-14
next time you install ubuntu on that machine when you get to the screen attached below hit F6. Choose noapic and it will be installed that way for you.  See [Boot Options]("https://help.ubuntu.com/community/BootOptions")

---

