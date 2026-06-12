---
title: "How to execute a script when my laptop starts running on battery?"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by gasull on 2007-02-11
Hi.

How can I automatically execute a script when my laptop starts running on battery, and another one when it starts running on AC?

Thank you in advance.

---

### Post by RandomJoe on 2007-02-11
Looking through /etc/acpi and /etc/acpi/events, it appears that /etc/acpi/power.sh is called whenever you go on/off AC power.  Reading through it, toward the bottom, I believe whenever switching to AC it will run any scripts contained in /etc/acpi/ac.d and vice versa when going to battery will run anything in /etc/acpi/battery.d

Hm, that could be useful...  Never noticed that before! :)

Caveat:  I think that's right, my shell scripting is a bit rusty and that's a first glance... ;)

---

### Post by ltmon on 2007-02-11
You are right RandomJoe.

Put a script in /etc/acpi/battery.d/

It will run in numerical order (e.g. 10-scriptname.sh will run before 20-scriptname.sh).

The script will run as the root user, so be careful.

---

