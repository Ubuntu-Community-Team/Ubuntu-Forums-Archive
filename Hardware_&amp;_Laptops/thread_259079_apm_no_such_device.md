---
title: "apm no such device"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by Nuno Morgadinho on 2006-09-16
I've just installed Ubuntu 6.06 LTS, Dapper Drake but can't get 'apm -s' to work. I get the following error even after removing all ACPI related stuff from the kernel:

$ sudo modprobe apm
FATAL: Error inserting apm (/lib/modules/2.6.15-26-386/kernel/arch/i386/kernel/apm.ko): No such device

I had APM support in my previous distro so I know the laptop supports it.

Can I avoid building a new kernel?

---

