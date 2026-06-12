---
title: "is 64-bit Lubuntu good for this laptop?"
date: 2018-01-20
forum: Hardware
---

### Post by ardouronerous on 2018-01-20
I have an Dell Inspiron E1505 running Lubuntu 16.04 32-bit, and I just found out that this laptop can run 64-bit;

```
lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Model name:            Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
Stepping:              6
CPU MHz:               1000.000
CPU max MHz:           1667.0000
CPU min MHz:           1000.0000
BogoMIPS:              3328.82
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
```

Here's the other specs:

1GB RAM (512x512MB DDR2 533MHz RAM)
120GB WD Green SSD

The current RAM of this laptop is 1GB (512x512), while this laptop's RAM is upgradeable to 2GB, I cannot upgrade it because I cannot find DDR2 RAM anymore, I don't have a credit card so shopping online is not an option.

Given the specs and limits, should I stick with Lubuntu 32-bit when 18.04 LTS comes along, or should I upgrade it to Lubuntu 64-bit?

---

### Post by mörgæs on 2018-01-21
You could install both in a dual boot and see which one works faster. My guess is that 32 bit performs better with only 1 GB of memory.

---

### Post by ardouronerous on 2018-01-21
The problem with 32-bit though is that it's being obsoleted by Canonical and according to what I've heard, Lubuntu 18.04 might be the last version to support 32-bit.

Doesn't having an SSD make a difference in performance despite only having 1GB RAM?

My dad uses this laptop and he usually visits Facebook and watches live feeds from Youtube.

---

### Post by mörgæs on 2018-01-21
What disappears is the standard 32 bit Ubuntu ISO which I wouldn't recommend anyway for your hardware. If you want a 32 bit Ubuntu and not one of the other Buntus it can still be installed if you begin from the minimal ISO.

The 32 bit Lubuntu carries on in 18.04 as always. I don't know what happens after that and it's also irrelevant for the problem right now.

---

### Post by ardouronerous on 2018-01-21
will Lubuntu 18.04 be supported til 2023? And if Lubuntu 18.04 is the last version to support 32-bit, is it possible to use it past it's EOL?

---

### Post by mörgæs on 2018-01-21
It will be supported through april 2021 and should not be used thereafter. Post again when we reach that date, there is no reason to believe that there will be no future Buntus for 32 bit.

---

### Post by DuckHook on 2018-01-21
> **ardouronerous said:**
> …is it possible to use it past it's EOL?
Nothing stops you from using an OS past its end of life except common sense. I still have XP and Vista running in VMs. Both (and XP in particular) are well past EoL. They are safe in my VMs because I introduce no new software and have disabled the virtual NIC. Therefore, they are completely isolated.

On the other hand, you have likely been following along on the recent Meltdown/Spectre fiasco. If you were running an obsolete OS right now&#8213;say, Ubuntu 10.04&#8213;how secure would you feel? It will never get updated to close off those holes. And as crackers start developing exploits to take advantage of those vulnerabilities, every site you visit will increasingly become an attack vector. If you are okay with doing your banking online with those vulnerabilites glaring at you, then I suppose running an EoL version is no big deal. I would never do it. But that's me.

So, it depends on your risk tolerance and how much you will be able to sandbox. If it will be your main OS that just has to have access to the big bad internet, then even though it's possible, it is a very bad idea.

---

### Post by ardouronerous on 2018-01-21
> **mörgæs said:**
> It will be supported through april 2021 and should not be used thereafter. Post again when we reach that date, there is no reason to believe that there will be no future Buntus for 32 bit.

I hope Lubuntu will support 32-bit past 18.04 to the next LTS verison.
Anyway, a lot can happen in 3 years, maybe I will be able to find DDR2 RAM for the laptop and be able to use 64-bit Lubuntu or the laptop could break down eventually making us look for a new laptop which will obviously be 64-bit, whatever comes first.

Question, if I do upgrade the RAM to 2GB, 64-bit will be good then?

> **DuckHook said:**
> Nothing stops you from using an OS past its end  of life except common sense. I still have XP and Vista running in VMs.  Both (and XP in particular) are well past EoL. They are safe in my VMs  because I introduce no new software and have disabled the virtual NIC.  Therefore, they are completely isolated.

On the other hand, you have likely been following along on the recent  Meltdown/Spectre fiasco. If you were running an obsolete OS right  now&#8213;say, Ubuntu 10.04&#8213;how secure would you feel? It will never get  updated to close off those holes. And as crackers start developing  exploits to take advantage of those vulnerabilities, every site you  visit will increasingly become an attack vector. If you are okay with  doing your banking online with those vulnerabilites glaring at you, then  I suppose running an EoL version is no big deal. I would never do it.  But that's me.

So, it depends on your risk tolerance and how much you will be able to  sandbox. If it will be your main OS that just has to have access to the  big bad internet, then even though it's possible, it is a very bad  idea.

Thanks for the warnings on EOL. If Lubuntu ends 32-bit support after 18.04, I will have to look for another distro that supports it or like I said earlier, either I manage to upgrade the RAM or the laptop breaks down, whatever comes first.

---

### Post by sudodus on 2018-01-21
64-bit Lubuntu will run well with 2 GB RAM

---

### Post by Yellow Pasque on 2018-01-21
> **ardouronerous said:**
> Doesn't having an SSD make a difference in performance despite only having 1GB RAM?
It's faster than a a hard disk, but it's not a complete substitute to RAM.
[https://superuser.com/questions/617864/why-not-use-ssd-space-as-ram](https://superuser.com/questions/617864/why-not-use-ssd-space-as-ram)

---

### Post by DuckHook on 2018-01-21
> **ardouronerous said:**
> I hope Lubuntu will support 32-bit past 18.04 to the next LTS verison&#8230;
FWIW, I operate an odd-duck MOBO that will only run 32-bit. Although the CPU is actually capable of 64-bit, the MOBO is restricted to 32-bit. If 32-bit disappears in all respects (including from the mini.iso) that will orphan my oddball machine. In spite of that, I would support Ubuntu if they made such a decision.

Ubuntu is so useful that, for most of us, it has become part of the background of our lives. But that means that we often lose sight of just how much cussed work goes in to developing it, maintaining it and improving it. Yet, it's free. Canonical finances its development using other means. I derive the massive benefit of it's use for the price of some learning and time investment. Pretty good deal.

But being free also means that Canonical's resources are limited. It means that they have to choose between devoting those very limited resources towards either improving 64-bit or maintaining 32-bit. I would rather they do the former and not the latter. If that means orphaning a perfectly good machine, then so be it. I notice that Google orphaning old Android phones barely raises a whisper. Likewise, Apple orphaning iPhone 3s or Microsoft orphaning any laptop older than 8 years old (all of which I have). And we *paid* for those.

Ubuntu has to keep up with the times. Old things have to die off. That's the way of the world. And I wouldn't want it any other way.

---

