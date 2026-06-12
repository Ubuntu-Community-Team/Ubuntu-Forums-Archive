---
title: "Processor family for Amd Athlon 64 X2 (k9)"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by Intrepid Ibex on 2009-10-11
Hi,

I'm installing a custom kernel and now I see a "Processor family" stage. I got Athlon 64 X2 (7750) processor, which is **K9** *(**E:** it's K10)* series but it's not on the list so I guess I should pick K8, right?
The default option was Pentium Pro, I guess because so many people got it or something.. 

If someone wants to see all the options, they are:

[LIST]
[*]386
[*]486
[*]586/K5/5x86/8x86/8x86MX
[*]Pentium-Classic
[*]Pentium-MMX
[*]Pentium-Pro
[*]Pentium-II/Celeron(pre-Coppermine)
[*]Pentium-III/Celeron(Coppermine)/Pentium-III Xeon
[*]Pentium M
[*]Pentium-4/Celeron(P4-based)/Pentium-4 M/older Xeon
[*]K6/K6-II/K6-III
[*]Athlon/Duron/K7
[*]Opteron/Athlon64/Hammer/K8[COLOR="White"]OOO[/COLOR][COLOR="Red"]**<-- This one(?)**[/COLOR]
[*]Crusoe
[*]Efficeon
[*]Winchip-C6
[*]Winchip-2/Winchip-2A/Winchip-3
[*]GeodeGX1
[*]Geode GX/LX
[*]CyrixIII/VIA-C3
[*]VIA C3-2 (Nehemiah)
[*]VIA C7
[*]Core 2/newer Xeon
[/LIST]

---

### Post by Intrepid Ibex on 2009-10-11
So in simplified my question is that: 
> which processor family should I pick from the list for my Amd 9K processor :).

---

### Post by AlphaLexman on 2009-10-11
> **Intrepid Ibex said:**
> 
[LIST]
[*]Opteron/Athlon64/Hammer/K8[COLOR=White]OOO[/COLOR][COLOR=Red]**<-- This one(?)**[/COLOR]
[/LIST]


I have an AMD Athelon 64 X2 6000, and that's the one I would choose, although I've never built my own kernel.

---

### Post by Intrepid Ibex on 2009-10-12
Yeah, probably the "sanest" choice :).

---

### Post by Intrepid Ibex on 2009-10-12
Just to prevent confusion, Athlon 64 X2 7750 seems to be K10, not K9 series :).

```
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control

```

---

