---
title: "Howto avoid C2/C3 CPU idle state ?"
date: 2009-11-24
forum: Hardware
---

### Post by ambrosa on 2009-11-24
I run Ubuntu 8.04.3 LTS server 32bit in a small low power motherboard (VIA LN10000EG) equipped with VIA C7 1GHz CPU
I've some problems with serial device: sometimes I've overrun errors when receive data through /dev/ttyS0

After some days of hard work I've discovered that when CPU enter in C3 state (very idle, with wake-up latency = 800 microsecond and internal cache loss) and data come in from serial line, I've the overrun.
Probably wake-up from C3 take loooong time.

I've searched for a solution and I've found that kernel parameter "idle=halt" avoid CPU enter C2/C3 state, but this parameter is not supported anymore.
So now I've completely disabled the ACPI support ("acpi=off" kernel parameter).

I have no problem to modify kernel source and recompile it.

The question is: Howto avoid CPU enter C2/C3 state and re-activate ACPI so CPU can go in C1 state ? C1 is better than nothing at all ;)

---

