---
title: "ACPI problem"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by tonyo46 on 2006-07-16
I have some problems with the temperature of my processor.
I had twice a "halt" forced because of a too high temperature (over 90° !).
I think there is a problem, because the fan was not running to prevent the temperature increasing !!
Another thing that make me think I have a problem is that the fan is functioning a little bit after the boot (when I launch process etc...), but after a little time, it doesn't turn any more even if I use all the power of my processor !!! so the temperature increases quickly.

How can I find where is my problem ?
how can I re-install acpi ?
My laptop is a HP dv1000 with a Centrino 1.6 GHz

Thanks for your help.

---

### Post by Hellkeepa on 2006-07-16
HELLo!

Please read the following thread, as it sounds that you have the same problem as outlined in there:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by tonyo46 on 2006-07-16
hello

thanks for your advice but I don't think it's the same problem, because the frequency scaling works well on my laptop.
I discovered another curious point :
```
cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

```
Why don't I have "throttling control" and "limit interface" ?

---

