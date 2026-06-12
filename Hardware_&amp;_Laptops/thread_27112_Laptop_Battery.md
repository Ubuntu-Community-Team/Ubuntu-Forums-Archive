---
title: "Laptop Battery"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by ctrlER on 2005-04-14
Hi, my laptop battery discharges very quickly. I think the main reason are disk writes every 5 seconds. Dont know howt to stop them. 
It's the syslog.
Removed postfix, cron, anacron.
i think laptop-mode is on but cant tell for sure.
Can someone help this newbie?

Thank you.

Ricardo (Portugal)

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=ctrlER]Hi, my laptop battery discharges very quickly. I think the main reason are disk writes every 5 seconds. Dont know howt to stop them. 
It's the syslog.
Removed postfix, cron, anacron.
i think laptop-mode is on but cant tell for sure.
Can someone help this newbie?

Thank you.

Ricardo (Portugal)[/QUOTE]

Is it an old laptop? You might need to use APM instead of ACPI.

---

### Post by ctrlER on 2005-04-15
It's fairly recent. It's 1.5yo.
It's a compal CL50 also know as acer travelmate 291.
1.4Ghz Pentium M. It lasts only 2h when it should last 3h.

---

### Post by luca_linux on 2005-04-15
Are you sure you are making use of intel speedstep features through a kernel cpufreq governor or through the userspace one of powernowd?

---

### Post by ctrlER on 2005-04-15
Yes, i have gnome cpu applet and it tells me about cpu speed. its 600 now and its in userspace, i wrote a script to make in lowspeed when i want it.
I think the problem here is the hd. but i cant tell for sure. what else may be consuming power than the hard drive and the cpu?

thank you.

---

### Post by luca_linux on 2005-04-15
Try to check through hdparm your hd configuration, especially the power management section.

---

