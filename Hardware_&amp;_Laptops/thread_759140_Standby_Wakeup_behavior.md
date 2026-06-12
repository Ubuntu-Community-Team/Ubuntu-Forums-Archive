---
title: "Standby Wakeup behavior"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by ckgreenman on 2008-04-18
Hello,  I've noticed an odd behavior with regards to standby and wakeup on my Toshiba 1905-S303 laptop.

Under Windows XP, the system goes to standby when I close the lid and when I open the lid it immediately resumes as expected.

However, under Ubuntu, when I close the lid it goes into standy (after editing the lidbutton event of course) but opening the lid doesn't do anything and I have to press the power button to resume.  

Does anyone know what the difference might be and if there is any way to mimic the Windows auto resume feature in Ubuntu?

My hardware is as follows:
Toshiba Satellite 1905-S303 
Pentium 4 @ 2.6Ghz
512 MB Ram
40GB HD
ATI Radeon Mobility M6 (LY) w/32MB Video RAM
I don't remember the BIOS but I do know it IS NOT the Toshiba proprietary BIOS and IS ACPI compliant.  If needed I can get the version and such.

I'm currently running Gutsy although I've seen the same behavior in pretty much every Ubuntu release since Dapper which is when I first started playing with it.  In each release I have to manually edit /etc/acpi/events/lidbtn and tell it to use sleep.sh instead of lid.sh.


Any suggestions would be greatly appreciated.

Thanks

---

