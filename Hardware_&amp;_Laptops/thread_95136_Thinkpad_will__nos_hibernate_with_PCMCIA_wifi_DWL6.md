---
title: "Thinkpad will  nos hibernate with PCMCIA wifi DWL650 inserted"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by shartrec on 2005-11-25
System : Breezy on IBM Thinkpad A21e.  I have actually upgraded the kernel (2.6.14-ck1) to allow ACPI as 3com 3c59x drive is broken in standard breezy kernel.

Problem:  Hibernate does not work if I leave my DWL-650 wireless lan PCMCIA card inserted when I try to hibernate (suspend to disk).  Without the card inserted the system hibernates with no problems.

Symptom: When going into hibernate state the card gets turned off and there is a lot of writing to disk, then the card comes back on and the system hangs at that point and needs hard reboot with the power button.

I have tried manually stopping hotplug(/etc/init.d/hotplug stop) and pcmcia (/etc/init.d/pcmcia stop)  but these have not helped.  Actually with pcmcia stopped the system did power off but did not hibernate correctly and did a normal cold boot when powered back on.

/var/log/syslog shows no differences, that I can find, between the successful and unsuccessful hibernate attempts.

---

