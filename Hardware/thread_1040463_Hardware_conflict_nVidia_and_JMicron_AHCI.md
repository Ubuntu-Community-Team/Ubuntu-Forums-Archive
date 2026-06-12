---
title: "Hardware conflict? nVidia and JMicron AHCI"
date: 2009-01-15
forum: Hardware
---

### Post by xuanyou on 2009-01-15
Hello,

I've still got a problem where the system keeps querying a hard drive that doesn't exist.

syslog shows that the system queries the hard drive about every 5 seconds, but sometimes goes into a loop (maybe every 15 minutes) which forces the whole system to slow down (spamming interrupts).

After some investigation, the problem seems to be between my nVidia card and the JMicron AHCI controller.

I've tried switching off AHCI in BIOS, but the ahci module still loads in ubuntu kernel. I'm using 2.6.27-9, Ubuntu 8.10.

I've attached syslog, lspci and /proc/interrupts for reference.

Anyone have any tips on how to solve this?

---

### Post by xuanyou on 2009-01-23
bump?

---

