---
title: "Pc doesn't shutdown with i686 kernel."
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by Skeletonix on 2006-06-19
**Hello...**

I have installed i386 and i686 kernel. Kernel i386 works fine, but when I boot i686 kernel I not able to shutdown PC. On console I see:  ```
[13145] Power off
``` and it's all, I must push button to shutdown PC .. :( ..

[color=navy]**Please** how can I shutdown PC with 686 kernel **?**[/color]

*My old PC:*
> CPU: P3-450MHz
MB: MS7112C VIA Apollo Pro 1330Mhz

ACPI doesn't work I use for power manegment apmd service.;)

---

### Post by ranf on 2006-06-20
If APM is used by the kernel it should work. Did you add something like "apm=on" to the kernel parameters?
What do you get here:
```
dmesg | grep APM
```

---

### Post by RawMustard on 2006-06-21
Same here, Asus P5AD2 Deluxe mobo running 2.6.15-25-686
 kernel will not shutdown.  Was working fine in Breezy!

---

### Post by mainekid on 2006-06-21
I am also having this problem with a MSI-Speedster 945gt mobo.

---

### Post by pmbuc on 2006-07-23
Just upgraded my Dell Inspiron 4000 laptop from Breezy to Dapper.

Boot stanza:
/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro  acpi=off apm=on quiet splash

$ dmesg | grep APM
[   66.161517] Dell Inspiron machine detected. Enabling interrupts during APM calls.

I still have to shutdown manually. Any ideas?

---

