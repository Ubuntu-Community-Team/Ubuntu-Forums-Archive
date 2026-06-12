---
title: "CPU scaling appled is not working for me?"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by Zingam on 2005-05-10
How can I make the CPU scaling applet to show me the actual CPU speed? It's not working on my Mobile P4.
Also is the an applet that shows the HDD temperature and other hardware status.

---

### Post by luca_linux on 2005-05-10
Are you sure that the right kernel modules providing the needed support are loaded?

---

### Post by Zingam on 2005-05-10
ACPI works, at least GNOME report the state of my battery.
I'm not sure if CPU throttling has anything to do with ACPI.

What modules are necessary for this to work?

---

### Post by luca_linux on 2005-05-10
p4-clockmode.ko.

---

### Post by Zingam on 2005-05-29
[QUOTE=luca_linux]p4-clockmode.ko.[/QUOTE]

how do I install this module?

I have updated to 686 kernel, I'm not using the default 386 and when I try to modeprobe it it cannot find it.

---

