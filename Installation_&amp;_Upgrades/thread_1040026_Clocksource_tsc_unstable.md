---
title: "Clocksource tsc unstable"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2009-01-15
I am trying to load ubuntu live cd and nothing happens after I hit start/install. I remove the quite splash thing and I see this message

Clocksource tsc unstable (delta = -299251584239ns)

what does that mean? I've been using the same cd for a while now and I know it works, plus I've installed ubuntu alot of times on my pc before using live cds. 


I'm running
Asus M2a-VN Mobo
AMD Athlon X2 +3600 1.9Ghz
OCZ 2 GB RAM 800Mhz DDR2
Plenty of disk space available

I heard from someone that it means my bios battery is running low. Could that be it?

---

### Post by Partyboi2 on 2009-01-15
Try adding clocksource=hpet as a boot option and see what happens. At the main menu press F6 and at the end of the line add ```
clocksource=hpet
```

---

### Post by polobreaka on 2009-02-13
bump, 

id like to keep this on top hoping someone can help with this. ive been researching this problem for 3 days and cant seem to find a good solution to it. 

im having random hang ups and after when the hang up is done, i check the log files and it would always come up as clocksource tsb unstable.

please help with this problem.

---

### Post by macabro22 on 2009-07-07
what about adding the option clocksource=jiffies to the kernel lines in /boot/grub/menu.lst?

---

### Post by mc_scRAT on 2009-07-16
[https://lists.ubuntu.com/archives/ubuntu-users/2009-February/175828.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-February/175828.html)
this tread rocks the question!

---

### Post by sirio81 on 2011-01-12
> this tread rocks the question
I think you pasted the wrong link. It's about thunderbird.
I have a virtualized karmic and I get lot's of

```
/var/log/kern.log:Dec 26 07:10:28 webmail kernel: [  615.503277] Clocksource tsc unstable (delta = -147977885 ns)
/var/log/kern.log:Dec 27 07:02:00 webmail kernel: [  107.000842] Clocksource tsc unstable (delta = -139962943 ns)
/var/log/kern.log:Dec 28 07:03:41 webmail kernel: [  208.502001] Clocksource tsc unstable (delta = -137181469 ns)
/var/log/kern.log:Jan 12 09:17:19 webmail kernel: [    8.035751] Clocksource tsc unstable (delta = -94509445 ns)

```

Did any of you tested the boot options reported above?
Which one works?

---

### Post by vmayakovski on 2013-02-04
Hi dear community!

#Thanks to you I'm getting with linux better and better (sry for my English).
#INow it's my turn to contribute a little piece of solving this "Clocksource tsc #unstable".

I've got freezes just after system has booted and there were messages like 
[INDENT]Marking TSC unstable due to cpu freq changes
Clocksource tsc unstable (delta = -96979.... ns)
[/INDENT]in /var/log/syslog.

Adding "notsc clocksource=acpi_pm" to kernel parameters didn't help.

The solution for me was switching "**AMD Cool'n'Quiet configuration**" to "**Disable**" feature in BIOS.

Linux rocks!):P

---

### Post by oldos2er on 2013-02-04
Old thread closed.

---

