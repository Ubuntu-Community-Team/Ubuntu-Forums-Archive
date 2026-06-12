---
title: "Spontaneous poweroff on IBM X31"
date: 2008-11-06
forum: Hardware
---

### Post by popefelix on 2008-11-06
I just installed 8.04 on my IBM Thinkpad X31.  Previously, it had been running 8.10 upgraded from 8.04 upgraded from 6.06, but the 8.10 upgrade somehow broke my X configuration.  Rather than troubleshoot it, I decided to back up all my important stuff and do a fresh install from the 8.04 CD I have.

This works well, except for one thing: every time I disconnect AC power, even with a full battery, after a few seconds the machine will spontaneously shut off.  It happens with both kernel 2.6.24-21-generic and 2.6.24-19-generic, in both multiuser (i.e. GDM) and single (i.e. runlevel 2) mode.

I've managed to prevent this behaviour by disabling ACPI on boot.  However, when I disable ACPI, my Thinkpad buttons (e.g. sound, brightness) don't work.  

Should I file a bug about this spontaneous poweroff behavior?

---

### Post by popefelix on 2008-11-29
I've just upgraded to 8.10 with kernel 2.6.27-9-generic, and this behaviour is still happening.

---

