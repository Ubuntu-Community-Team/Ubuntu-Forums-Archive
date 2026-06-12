---
title: "Thinkpad not shutting down"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by grinchy on 2005-09-28
I have a Thinkpad T21 running ubuntu 5.04.
The problem i have is that no matter which of the options i pass the shutdown command the computer never actually powers off. It's a really pain in the ass and I have no idea how to tackle it.
Has anyone had the same sort of problem or have any suggestions?

---

### Post by mlomker on 2005-09-28
> Has anyone had the same sort of problem or have any suggestions?

Where does it stop?  What's on the screen?  I'm not sure if I have an answer, but some more details would help.

---

### Post by grinchy on 2005-09-29
Sorry of course.

One of two things happens

1) the computer goes through it's normal shutdown procedure until power down appears on the screen, then it just stops. I can hear the disks  being shut down but nothing else happens

2) The screen goes mad and starts flashing different colours at me, computer does stuff for a while -- presumably the full shutdown procedure -- and then disks shutdown and screen keeps flashing at me.

---

### Post by mlomker on 2005-09-29
That sure seems strange.  The shutdown process uses standard power management commands to the BIOS to tell it to shut off.  I know the T-series aren't very old but have you checked with Lenovo/IBM to see if there is an updated BIOS version available?  I'm not sure if you've made many adjustments in the BIOS but resetting to defaults might be worth a shot if there is an option to do that.

---

### Post by grinchy on 2005-09-29
No havn't changed the bios that much and as far as i know there is no bios update.

If i just use the halt command the system shuts down and powers off almost instantly

I'm looking at changing /etc/init.d/halt maybe

---

### Post by grinchy on 2005-10-05
Does anyone have any ideas?

---

### Post by knappen on 2005-10-06
I am using a T21 without any problems at all.

Try to add "acpi=off apm=on" as a boot option in grub.

T21 does not use ACPI, it is basically an APM machine.

If the above does not work, try to add "noapic" as well.

Please let us know if it works out for you.

---

### Post by grinchy on 2005-10-10
Cheers i'll try that and get back to you.

---

