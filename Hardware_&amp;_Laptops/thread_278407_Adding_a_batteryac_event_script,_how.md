---
title: "Adding a battery/ac event script, how?"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by quini on 2006-10-16
Hallo!

I was wondering how to run a script when changing from battery to ac or viceversa; for instance I'd like the following to be run when changing from ac to battery:

*iwconfig eth1 power on powertx 10*

And from battery to ac:

*iwconfig eth1 power off powertx auto*

TIA  ;)

---

### Post by Woei on 2006-10-16
> **quini said:**
> Hallo!

I was wondering how to run a script when changing from battery to ac or viceversa; for instance I'd like the following to be run when changing from ac to battery:

*iwconfig eth1 power on powertx 10*

And from battery to ac:

*iwconfig eth1 power off powertx auto*

TIA  ;)

There are already scripts that run when either of these two events occur. See /etc/acpi/events/{ac|battery}. Basically, you'll want to add a one-liner script containing the above two commands in respectively /etc/acpi/ac.d/ and /etc/acpi/battery.d/. They will be called by /etc/acpi/power.sh.

---

### Post by quini on 2006-10-16
Hey!  That was simple  :p 

Thanks!  ;)

---

