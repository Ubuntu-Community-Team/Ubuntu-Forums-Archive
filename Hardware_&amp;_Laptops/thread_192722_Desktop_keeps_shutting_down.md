---
title: "Desktop keeps shutting down"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Ted_Smith on 2006-06-09
I leave my Desktop running 24\7 and it's always been fine, except recently I had to re-install Breezy. ever since, I keep coming down in the morning and find that it's tunred itself off. 

I've looked in a few logs (/var/logs/kernlog, syslog) to see what the very last entries where in them. 

This was at 10:25pm in kernlog: 
```

Jun  8 22:25:15 localhost kernel: [4299034.584000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jun  8 22:25:15 localhost kernel: [4299034.584000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jun  8 22:25:15 localhost kernel: [4299034.584000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
Jun  8 22:25:36 localhost kernel: [4299056.369000] APIC error on CPU0: 08(02)

```

This was at 00:12 a few hours later in the early hours of this morning in syslog : 
```

Jun  9 00:12:49 localhost dhclient: DHCPACK from 192.168.1.1
Jun  9 00:12:49 localhost dhclient: bound to 192.168.1.5 -- renewal in 1415 seconds.
Jun  9 00:17:01 localhost /USR/SBIN/CRON[14215]: (root) CMD (   run-parts --report /etc/cron.hourly)

```
 
I'm not sure what other logs may reveal anything of interest (I assume there's no event viewer in Ubuntu?) but does the above help anyone understand what the problem might be? Incidentally, I run a grid computing project which uses CPU cycles to process cancer data, but I ran that before using Breezy and it was always fine. 

Ted

---

### Post by Jussi Kukkonen on 2006-06-09
> I'm not sure what other logs may reveal anything of interest (I assume there's no event viewer in Ubuntu?)
*System Log* in *System-->Administration*. It's just the same log files in a GUI, though.
> but does the above help anyone understand what the problem might be?
Not that I can see. Does this happen every night?

---

### Post by Ted_Smith on 2006-06-09
It seems to, yes, but I've not monitored it closely enough. 

I am just in the process of upgrading to Dapper from breezy to see if that helps at all. 

Anymore ideas in the meantime appreciated. 

Cheers

Ted

---

### Post by Ted_Smith on 2006-06-20
I've tunred off APIC in the boot loader by adding 'noapic' and 'nolapic' to the kernel entries. So far, so good. It's been up for a few days doing number crunching exercies without any problems. I also don't get any error messages when I run 'dmesg | tail'

---

