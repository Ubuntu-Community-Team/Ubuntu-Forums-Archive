---
title: "hdparms not reset after resume"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by steini on 2006-06-04
First things first: My laptop is an Acer TM 800.

I have enabled LAPTOP_MODE in /etc/default/acpi-support, and then modified /etc/laptop-mode/laptop-mode.conf so my harddisk would idle even if connected to AC.
However, after a suspend (to RAM) ... resume cycle, these idle spin down times are not reset, so the harddisk stays on.
I had a look at /etc/acpi/*, and noticed that in resume.d/ there's a script that calls power.sh. power.sh however uses its own hdparms settings, and does not honor the values in laptop-mode.conf. Why's that? In addition, that power.sh script doesn't actually do anything upon resume, I guess, as the power status does not change. So no reinitialization is done.

So, why are there two conflicting places for the idle spindowns? And what would be a good place to reinitialize the spindown timeouts? Would I put a new script in /etc/acpi/resume.d that does a laptop-mode restart?

---

