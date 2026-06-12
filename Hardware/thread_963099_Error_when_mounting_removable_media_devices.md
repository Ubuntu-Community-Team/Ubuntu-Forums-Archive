---
title: "Error when mounting removable media devices"
date: 2008-10-29
forum: Hardware
---

### Post by thegrayarea on 2008-10-29
I am getting the error below when i plug a removable media devices in to my laptop with ubuntu on it. 

[IMG]http://leovilletownsquare.com/uploads/med_1225334258-error.jpg[/IMG]

Any idea's on how to fix it?

---

### Post by cariboo on 2008-10-30
WHat is the output of dmesg when you plug your device in? Open a terminal and type:

```
tail -n 10 /var/log/dmesg
```

This will print out the last 10 lines of dmesg. Paste the output in your next post.

Jim

---

### Post by thegrayarea on 2008-10-30
> **cariboo907 said:**
> WHat is the output of dmesg when you plug your device in?
Jim

```

[   22.207220] cs: IO port probe 0xa00-0xaff: clean.
[   22.648054] intel8x0_measure_ac97_clock: measured 55253 usecs
[   22.648058] intel8x0: clocking to 48000
[   23.193928] lp0: using parport0 (interrupt-driven).
[   23.306993] Adding 1502036k swap on /dev/sda6.  Priority:-1 extents:1 across:1502036k
[   23.953995] EXT3 FS on sda5, internal journal
[   24.950385] type=1505 audit(1225380238.959:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3993
[   25.200102] type=1505 audit(1225380239.211:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3998
[   25.200505] type=1505 audit(1225380239.211:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3998
[   25.405949] ip_tables: (C) 2000-2006 Netfilter Core Team

```

I am wondering if its an issue with my hard drive, i know a failing hard drive can cause weird issues with the OS. Cause the same thumb drive works on my Desktop.

I am using the most up to date version of Ubuntu 8.10, Last update i did was tuesday

---

### Post by thegrayarea on 2008-10-31
bump!!!

happy halloween

---

