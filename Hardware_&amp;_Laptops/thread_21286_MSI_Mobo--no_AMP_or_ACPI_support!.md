---
title: "MSI Mobo--no AMP or ACPI support!?"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-03-21
I just upgraded to an MSI Neo2 FISR (with the 865PE chipset). I'm using a P4 3.2E, and some new memory. Other that, my setup is the same as before (when I had a dual AMD board), only now, **when I use the halt command, the computer won't shut all the way off!**

This is kind of bad; I have lm_sensors set up to halt the machine if the temps go above 83 degrees--which is necessary, since I have a watercooling system, and if my pump dies while I'm not home, then my entire system goes with it :| 

I've looked around the forums, and some people had the same problem, but when they upgraded to Hoary, their problems melted away.

Anyone have any advice? Thx in advance;)

---

### Post by ming0 on 2005-03-23
I looked in BIOS, and I seem to have the necessary stuff selected.
Here's what my problem looks like:
 ```
dean@dim:~$ lsmod |grep acpi
pcc_acpi			   11008  0
sony_acpi			   5928  0
dean@dim:~$ lsmod |grep apm
dean@dim:~$ sudo modprobe apm
Password:
FATAL: Error inserting apm (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/apm.ko): No such device

``` 
And when I use the halt command, the computer halts and ends by saying "power down" but never actually powers down.

Do I need to totally unload acpi before I can turn APM on?

---

