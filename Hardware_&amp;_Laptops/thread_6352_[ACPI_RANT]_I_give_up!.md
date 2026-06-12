---
title: "[ACPI RANT]: I give up!"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by jdong on 2004-11-27
Heh, well, on Black Friday I got a nice $500 Toshiba laptop from Best Buy, hoping to put Linux on it... (m35x-S109)


I started with Ubuntu (duh), but eventually did try Fedora and SuSe 9.1.

Well, unfortunately Linux isn't here to stay on this laptop. The reason: poor ACPI support. Suspend-to-RAM doesn't function _at all_, which ticks me off -- I'm an on-and-off laptop user, flicking the Fn+F3 suspend sequence frequently through a day's work. As I speak, I'm still on my 1st charge, with 16% life remaining. With XP, this laptop can go in& out of standby in less than 5 seconds combined -- very convenient.

With Linux, standby works, but I can't resume. It's not an fb issue, not X -- I started in bare-bones init=/bin/bash mode, and I still can't get resume to function properly. I decided to apply patches for acpi from -mm & acpi.sf.net -- still no luck. Installed Mandrake 10.1's kernel ("enhanced ACPI support"), same problems.


However, swsusp2 works, but it takes ~30 seconds to suspend and resume with a hefty 768MB RAM to manage!

In the end, I loaded XP back on the laptop, left 8GB of Linux experimental space (currently occupied by Ubuntu).

If Linux wants to be a contender with Windows, it really needs good ACPI support.

---

### Post by daniels on 2004-11-28
To be fair, this is often neither the fault of Linux nor ACPI -- it's the manufacturers making horrifically broken support and knowing that they can just hack around it in Windows drivers.  ACPI information tables (DSDTs) often blatantly lie, and to be fair, given the amount of debugging and stuff that needs to be done, Linux has done an amazing job of supporting laptops to the degree it does.  But, that being said, I agree it really does suck that it doesn't support your laptop.

---

### Post by jdong on 2004-11-30
Sorry, I guess at the time I was too heated up with frustration to realize how much work has already been put into ACPI, and how it does work for others.

---

### Post by zenwhen on 2004-11-30
They had to cut corners in some places to get that price down. Not following the ACPI specs seems to have been one of them.

---

