---
title: "Acer ES1-311 no fan control, stops after resume."
date: 2016-04-05
forum: Hardware
---

### Post by martin194 on 2016-04-05
Hello.

**Setup:** Acer ES1-311 brand new, latest BIOS V1.11
**Tested:** Ubuntu 14.04 x64, Xubuntu 16.04 x64

**Current kernel:** 4.4.0-16-generic
[B]
Issue:[/B] The fan just runs, there is no temperature or load based throttling.
**Problem**: Suspend system and resume, fan runs on 100% for a second and then completely stops leaving the system without any cooling.

I thought I give 'acerhdf' a try, but a modprobe fails:
[FONT=lucida console]acerhdf: unkown (unsupported) BIOS version Aver/Aspire ES1-311/V1.11, please report, aborting![/FONT]

I also tried to get [NBFC]("https://github.com/hirschmann/nbfc") running with mono, no luck, couldn't get it to compile.

So is there a Kernelbug resulting in the fan to stop working, or is there any tool to manually/automatically my machines fan?

---

### Post by martin194 on 2016-04-15
Quick update, now running 4.4.0-18-generic, same behaivior.

---

