---
title: "Gateway nx860xl ACPI problem"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by James_mtl on 2007-12-27
Look like I'm having problem getting power management working properly on this laptop.
Big problems is fan.  They run constantly on AC which I can live with but the problem is they don't run at all on battery !!  Temperature keeps increasing until it reach critical and shutdown; not very practical ! 

I did some reading but nothing to ix my problem yet.  Can someone with more eperince then me point me in the right direction.

I'm running 7.10 and every other acpi functions seem to work properly; battery info, cpu throttling etc ... 

I tried booting with acpi=off; it does solve my fan problem but I loose all other acpi function; plus not knowing remaining battery life render the fact that I can actually use my laptop on batteries not practical.

sensors-detect does not find any fans and I do not have anything under /proc/acpi/fan ( which I read that it could be normal ).

I do get this error while booting : ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

I did follow online instruction on recompiling my DSDT file and it did not give me any errors 

I have a DSDT.aml file just don't know where to save it to fix this error ( don't even know if it will fix my problem ). 

My bios is the latest for this laptop 72.15 ( in fact it's not even on gateway download ?? they list 72.14 as the latest ?? )

Any body with a nx860 serie laptop with fan working properly under batteries ?

Thanks for your help,

---

### Post by IBG on 2007-12-27
> **James_mtl said:**
> Lo
I do get this error while booting : ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

I did follow online instruction on recompiling my DSDT file and it did not give me any errors 

Hi,
That's not an error it just tells you that there is no custom dsdt file in the initram.
And since you don't get any error while compiling your dsdt you should not have one.
I can't help you concerning the others issues.

---

