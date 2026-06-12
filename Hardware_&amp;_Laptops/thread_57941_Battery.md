---
title: "Battery"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by andlinux on 2005-08-18
I installed Ubuntu and everything works fine on my laptop, but there is one thing that's working badly and that is I think the power management.

Normally I can work on my laptop about 4-5 hours without reloading the battery but now it is 2 hours if I don't do things that require a lot of cpu power.

If I do "lsmod" then I see that the speedstep_centrino module is loaded and I installed a little program to see what the frequency is from the cpu and that is dynamically. Before Ubuntu I used Suse and I  could work also 4-5 hours on one battery.
I see that an acpi module (pcc_acpi) module is loaded is that better than apm ?

So what can I do to fix this problem ?

---

### Post by drizek on 2005-08-18
[QUOTE=andlinux]I installed Ubuntu and everything works fine on my laptop, but there is one thing that's working badly and that is I think the power management.

Normally I can work on my laptop about 4-5 hours without reloading the battery but now it is 2 hours if I don't do things that require a lot of cpu power.

If I do "lsmod" then I see that the speedstep_centrino module is loaded and I installed a little program to see what the frequency is from the cpu and that is dynamically. Before Ubuntu I used Suse and I  could work also 4-5 hours on one battery.
I see that an acpi module (pcc_acpi) module is loaded is that better than apm ?

So what can I do to fix this problem ?[/QUOTE]
 i use ksysguard(included with kdebase IIRC) and it shows you how much power your laptop is using in mA, the clock speed and the remaining battery power. use it to see how ubuntu manages your cpu and find processes which use a lot of cpu. post your mA ussage as well to compare it to others(mine is between 1300-1800 under low cpu, depending on screen brightness).

also, afaik, acpi is better for newer laptops(like centrinos) than apm.

I can post my ksysguard config if you want.

---

### Post by andlinux on 2005-08-19
[QUOTE=drizek]post your mA ussage as well to compare it to others(mine is between 1300-1800 under low cpu, depending on screen brightness).

also, afaik, acpi is better for newer laptops(like centrinos) than apm.

I can post my ksysguard config if you want.[/QUOTE]

If I want to see the battery, It says "error load the battery acpi module or compile it in your kernel"

But how can I post my mA ussage here, i don't see it in ksysguard ?

---

