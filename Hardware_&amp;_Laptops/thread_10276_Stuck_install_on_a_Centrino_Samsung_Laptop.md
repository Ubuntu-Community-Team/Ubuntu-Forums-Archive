---
title: "Stuck install on a Centrino Samsung Laptop"
date: 2005-01-06
forum: Hardware &amp; Laptops
---

### Post by physh on 2005-01-06
Hello everybody,
I'm trying to install Ubuntu on my laptop but the installation hangs at the very beginning.

The last three lines on the screen are :

PCI : Using configuration type 1
mtrr : v2.0 (20020519)
ACPI : Subsystem revision 20040816

And the nothing....

What can I do ?

My laptop :
Samsung P35 / Pentium M 725 / 512mb / 60gb / Ati radeon mobility 9700

---

### Post by physh on 2005-01-06
[QUOTE=physh]Hello everybody,
I'm trying to install Ubuntu on my laptop but the installation hangs at the very beginning.

The last three lines on the screen are :

PCI : Using configuration type 1
mtrr : v2.0 (20020519)
ACPI : Subsystem revision 20040816

And the nothing....

What can I do ?

My laptop :
Samsung P35 / Pentium M 725 / 512mb / 60gb / Ati radeon mobility 9700[/QUOTE]
 I answer to myself : linux acpi=off but I don't understand why I had to do this...

---

### Post by ardan_76 on 2005-01-17
hello physh,
3 weeks ago I got my Samsung P35 XVM 1600 III which is nearly the same model. At first I tried Debian, but have switched to Ubuntu this week. So I know some of the problems ...

The problem is not ACPI, but APIC. So when trying to boot up from the CD you should use the parameters "noapic nolapic" and ACPI will work fine. 
I need ACPI (modprobe asus_acpi) to get wlan working, because of this little button that turns wlan off. It just won't work without the asus_acpi module.

Why or what the APIC problem is, I don't know. I just found this solution somewhere else. Try google: P35 linux

---

