---
title: "The laptop's fan in Ubuntu vs. WinXP"
date: 2008-08-14
forum: Hardware
---

### Post by raynevandunem on 2008-08-14
I'm not going to ask about trying to keep the laptop from running hot, since it does that when running WinXP, but I just wanted to know about how to get the fan to quiet down once it boots into the splash screen in Ubuntu.

I think I read about lm_sensors, but I'm not to keen on whether it controls the loud running of the fan or the heat of the laptop overall.

So is there any other way to force the fan to quiet down when it boots into Ubuntu in the same way that it quiets down once it boots into the Windows splash screen? Or is there a lack of firmware/BIOS access by the Linux kernel that would stymie any solution to a quieter fan?

PS: This also affects the desktop as well. Both are from HP and have this same issue.

Desktop (2003): [http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&lang=en&product=366140&dlc=en&](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&lang=en&product=366140&dlc=en&)
Laptop (2006): [http://h10025.www1.hp.com/ewfrf/wc/product?product=3245620&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=3245620&lc=en&cc=us&dlc=en&lang=en&cc=us)

---

### Post by p_quarles on 2008-08-14
How long does it run after booting up? Generally speaking, I've found that fans work pretty properly and reliably in Linux, so it may just be that the fan is needed more during the Linux bootup than in the Win bootup.

But, you could take a look around the files in /proc/acpi/fan and /proc/acpi/thermal_zone. These will tell you how the system is defining various thermal states and when it turns the fan on. If these are consistent with the CPU temp when the fan switches on and off, it's behaving as it should. If there's a significant divergence, you may well have BIOS problems.

---

### Post by raynevandunem on 2008-08-18
It runs continuously after it hits the splash screen, and doesn't stop until you shut down either computer.

Furthermore, I don't know if it's the fan or something else that makes the "booting" noise in either mode. The sound just won't reduce in Ubuntu (or most Linuxes that I've tried...I think the only other operating system that has gone quiet after booting was Darwin, which I had mistakenly installed several years ago under the impression that it was an OSx86 .iso), just in Windows.

Also, if this is a fan issue (and it may be the CPU fan or the hard drive, I dunno), then I would like to note that the heat on the laptop doesn't reduce in either WinXP or Ubuntu, since the touchpad is usually and annoyingly hot (at which point I know that it has been on for more than a few minutes). So it's not necessarily a heat issue, just a hardware management issue.

I can only think of the following components that could have this issue in Ubuntu on either computer:

[LIST]
[*]the CPU fan
[*]the other fan that spews hot air (and alot of dust) out of a vent
[*]the hard drive
[*]?
[/LIST]

---

