---
title: "Can an ATX system be as efficient or nearly as efficient as a NUC, Brix, Mini ITX etc"
date: 2016-01-30
forum: Hardware
---

### Post by ultragamer2 on 2016-01-30
I want to make an atx home theatre pc that is super efficient for playing youtube videos and blu-rays, recording tv etc. Hopefully using a case and psu I have already (core2duo era).

Could it be made nearly as efficient as a modern small form factor pc like an intel nuc, brix or mini itx etc.? Would a psu from that era be very inefficient compared with todays psus?

If so what motherboard / cpu combination would be suggested? Celeron?

---

### Post by weatherman2 on 2016-01-30
Modern PCs - even those in regular-sized towers - consume shockingly little power at idle.  I have a "watt" meter and it's interesting to see how much power various devices use.  I have found that my Sandy Bridge and Ivy Bridge CPU boards (2nd gen and 3rd Gen Intel "core" processors like i3, i5, etc.)  consume anywhere from 15 to 30 watts at idle - and only maybe 40-50 watts under load.  The 400Watt + power supplies I use for them (because they are cheap) are way more than required.

A NUC will use less, but the amount of power saved is probably negligible as you can see.  The big benefit of something like a NUC is size and quiet operation, not power savings.

"Celeron" is now a marketing name for Intel, not a type of CPU.  They have used it for various different CPU families over the last few years.  Now Intel seems to use it for the ultra-low power netbook-type of CPUs like Bay Trail M (the "Atom" family) that are efficient but also pretty slow.  One of my older "Celeron" CPUs is a 2nd Gen (Sandy Bridge) dual core low power CPU, faster than the newer "Celerons" that are years newer.

Faster Intel CPUs don't necessarily consume much more power than the slower ones.  They are all designed to "clock down" the parts of the CPU that aren't in use, to save power.  You can compare the power specs (TDP) of any CPU to compare it to another one.  TDP is really the package specs - the maximum power the package the CPU is in is designed to dissipate.  The CPU itself may use much less than that.

Get an "80+" efficient power supply if you want an efficient one.  They use less power even at idle than those old "inefficient" cheap power supplies.  Some of my old towers with old power supplies used 5-6 watts at idle even with power off!  The new efficient PSUs use much less than 1 watt when powered off.

You can use an old case if you want for a new build.  The biggest missing piece may be lack of USB 3.0 front panel ports.

---

### Post by fkkroundabout on 2016-01-31
well generally laptops use alot less power than desktops - as they have to, to avoid draining the battery rapidly. so they use processors in laptops that are a chunk less powerful but alot more power efficient.

so any mini desktop computer that uses laptop grade parts (such as the mac mini and a variety of others on the market) will use many times less power.

basically the main thing to watch is the processor and the power supply. the way to make the computer efficient is to find a close balance between how much power the computer actually needs, and the maximum and overall efficiency of the power supply. so that means if all the components need 100W then a 500W power supply will generally waste more energy than a 200W power supply. AMD processors are generally more wasteful with power than intel processors, but there are low power AMD processors that are quite efficient

you also want a suspend option, which means the current state of the computer is saved to RAM and the motherboard is able to put the computer to sleep into a very low power mode when inactive for a chosen amount of time. the cheapest motherboards may not support this, but generally most motherboards do.

---

