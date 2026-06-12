---
title: "ACPI Issues with Gnome-Power-Management"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by gene6482 on 2007-04-18
I've been having issues with my Toshiba laptop that I've just recently ditched Vista to upgrade to Ubuntu on.  I had to manually edit my DSDT file so that I could get my sound working, but since I've done that, Gnome Power Manager doesn't work.  Here's the weird part.  If I go to a terminal and type in acpi -V, it shows all the information that I should be able to see in gnome.  Any help would be greatly appreciated.

---

### Post by gene6482 on 2007-04-19
bump

---

### Post by FluffyLogic on 2007-04-19
I'm having a similar problem. I went into system/services and disabled power management apm and acpi to test something, and then re-enabled it. 

Ever since I've been re-enabled, the icon for power manager 2.16.1 has an X through it, and always reports the laptop running on AC power.

Before I did the brief services twiddle, it worked perfect. Can anyone help me get back to a running state? If I try to add the battery charge monitor, it says it cant read from /var/run/acpid.socket.

---

### Post by gene6482 on 2007-04-19
it was the exact same set of circumstances that i experienced.  I'm probably going to do a fresh feisty install anyway, but it would be good to know the answer in case i don't

---

### Post by FluffyLogic on 2007-04-20
Okay, I can get gnome-power-management to work if I do the following:

1) restart dbus; this causes gnome-power-management to quit because it loses connection
2) start gnome-power management again

This probably has to do with the order in which things are starting. Can someone help me figure out how to diagnose this, and how to change the order which services are getting started under gnome?

---

### Post by gene6482 on 2007-04-20
i just reformatted and now it works

---

