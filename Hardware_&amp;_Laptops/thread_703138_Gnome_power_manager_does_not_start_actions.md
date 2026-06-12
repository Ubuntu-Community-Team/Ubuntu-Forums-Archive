---
title: "Gnome power manager does not start actions"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by fbn on 2008-02-21
Hi,

I have configured Gnome power manager to put the computer to sleep when inactive for 3 minutes.

The display should go to sleep when inactive for 2 minutes.

This is what happens:

After 30 seconds the display dims (that's a BIOS setting).
After 2 minutes the display gets blank (blank instead of dim, don't know why).
After that, nothing happens (but it should suspend after 3 minutes).

I have the same problem with the action for critically low battery, it should hibernate but it does nothing and powers off if the battery is out.

It seems that Gnome power manager is using the settings for display (dim) but is ignoring the actions (sleep if inactive, hibernate if low battery).

I've attached a screenshot of my configuration. Is this a bug or am I misunderstanding something here?

Frank

---

### Post by Yellow Pasque on 2008-02-21
What kind of computer do you have? Often, the computer will use ACPI for power management and ignore the GNOME settings.

---

### Post by fbn on 2008-02-21
I have a Dell Laptop (XPS M1330). Suspend and Hibernate work if I manually start them. Only Gnome power manager actions are ignored ...

---

