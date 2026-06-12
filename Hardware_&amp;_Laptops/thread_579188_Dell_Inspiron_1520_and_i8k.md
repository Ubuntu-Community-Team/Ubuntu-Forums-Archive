---
title: "Dell Inspiron 1520 and i8k"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by Gunner_Sr on 2007-10-18
I have installed i8k on Feisty on my dell 1520. When I look at i8kmon -v I get the following information.

i8kmon v1.27 17/06/2005 - Copyright (C) 2001 Massimo Dal Zotto <dz@debian.org>
config(0)          = {0 0} -1 60 -1 65
config(1)          = {1 0} 50 70 55 75
config(2)          = {1 1} 60 80 65 85
config(3)          = {2 2} 70 128 75 128
config(auto)       = 0
config(daemon)     = 0
config(geometry)   = 
config(i8kfan)     = /usr/bin/i8kfan
config(min_speed)  = 2000
config(proc_ac24)  = /proc/acpi/ac_adapter/0/status
config(proc_ac26)  = /proc/acpi/ac_adapter/AC/state
config(proc_apm)   = /proc/apm
config(proc_i8k)   = /proc/i8k
config(sysconfig)  = /etc/i8kmon
config(t_high)     = 80
config(timeout)    = 5
config(unit)       = C
config(userconfig) = ~/.i8kmon
config(verbose)    = 1
1192688641 opening /proc/i8k
1192688641 opening /proc/acpi/ac_adapter/AC/state
1192688641 acpi: state:                   off-line
1192688641 1.0 A03 HC9Y9D1 50 -22 0 922 0 0 -22
1192688641 1.0 A03 HC9Y9D1 50 -22 0 922 0 0 -22
1192688646 1.0 A03 HC9Y9D1 50 -22 0 922 0 0 -22
1192688651 1.0 A03 HC9Y9D1 50 -22 0 922 0 0 -22

I notice that the right fan is spinning and I can seem to control it, that is shut it off or increase it, is this a know bug, if so how can I get it logged or get a newer version of i8k?

Thanks in Advance.

---

### Post by Gunner_Sr on 2007-10-18
Bump

---

