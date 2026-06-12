---
title: "Laptop always crashes when battery is unplugged"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by ewdp on 2005-12-21
It's a Toshiba Tecra M3 Laptop.
Basically the system is very stable whether I'm on AC Power or battery mode as long as the battery is on the machine.
When I unplug the battery(I prefer to work this way), that's where the problems occur.
The machine just shuts down everytime in Gnome session(sometimes during boot time).
Anyone experienced a similar problem before?

I'm using the 2.6.12-10-686 kernel with acpi enabled.

Any help would be appreciated.
Thanks in advanced.

---

### Post by 23meg on 2005-12-21
That's strange. Look into your system and kernel logs for possible errors reported just before crash.

What's your processor? Do you have powernowd running? See if you still have the problem after killing it.

---

### Post by ewdp on 2005-12-21
Thanks for the quick reply, 23meg.
/var/log/messages or /var/log/syslog indicates nothing, I've checked this before.
Processor is Intel Pentium M 2 GHz.
I'll try your idea by disabling powernowd.

Thanks

---

