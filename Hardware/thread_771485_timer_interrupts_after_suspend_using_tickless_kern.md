---
title: "timer interrupts after suspend using tickless kernel"
date: 2008-04-27
forum: Hardware
---

### Post by zwalters on 2008-04-27
Using Hardy on an HP dv6324us (amd64 processor), if I run itop immediately after booting, I register something like a hundred interrupts per second, with no timer interrupts.  However, if I suspend the laptop and bring it out of suspension, itop registers ~250 timer interrupts per second.  The relevant line is

INT                NAME          RATE             MAX
  0 [PIC-edge      time]   251 Ints/s     (max:   252)

How does one set up the system to leave suspend in the same low-interrupt state as is reached from boot?

---

