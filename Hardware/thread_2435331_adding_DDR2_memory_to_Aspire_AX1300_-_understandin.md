---
title: "adding DDR2 memory to Aspire AX1300 - understanding limits"
date: 2020-01-19
forum: Hardware
---

### Post by crackers_altitude on 2020-01-19
I have a machine that needs more DDR2 memory in an Acer Aspire AX1300 desktop. My best understanding of this - from extensive searching on the Acer website especially - is there are two DIMMs on the motherboard. That's fine, I understand that. But then there are some user groups that mention how the limit is 4 GB total. This is frustrating because there are DIMMs available that allow 4 GB per DIMM, for a total of 8 GB. Perhaps there is a clue on the motherboard itself - I'll try to get that info ASAP [UPDATE : BIOS last update was 06/10/2010 - the DIMMs add up to 2048, but no MB info] - but in the meantime - until I open the machine - where might I find out about a supposed limit to how much memory this machine can take - will this show up in the system information? I suspect the motherboard simply doesn't handle more than 4 GB - the C|NET page for it says "max supported size" :

[https://www.cnet.com/products/acer-aspire-x1300-u1801a/](https://www.cnet.com/products/acer-aspire-x1300-u1801a/)

... perhaps there weren't 4 GB DIMMs available at the time of manufacture, so that's why it says "max supported size"? or the Windows software that was on it?

lsb_release, uname, /proc/meminfo, and other information :

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
Linux myAspireAX1300machine 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
cat /proc/meminfo 
MemTotal:        2814096 kB
MemFree:         1091048 kB
MemAvailable:    1552304 kB
[ truncated]

/proc/cpuinfo
processors 0-1 :

vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Athlon(tm) 7450 Dual-Core Processor
stepping    : 3
microcode    : 0x1000095
cpu MHz        : 1200.000
cache size    : 512 KB
[truncated]
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate vmmcall npt lbrv svm_lock
bugs        : tlb_mmatch fxsave_leak sysret_ss_attrs null_seg spectre_v1 spectre_v2

---

### Post by Frogs Hair on 2020-01-19
To get the motherboard model, you can install hardinfo and go from there. Different board vendors can be used for the same model of computer. I have an older board with a 2x4 GB maximum. ```
sudo apt install hardinfo   
```

---

### Post by him610 on 2020-01-19
Well crackers_altitude,
You probably don't want to read this - bad news.
This website, [https://www.cnet.com/products/acer-aspire-x1300-u1801a/]("https://www.cnet.com/products/acer-aspire-x1300-u1801a/") indicates maximum RAM for your system is 4 GB. That's it; maximum RAM is determined by the motherboard. If you want more RAM, you will need to upgrade your motherboard (and probably CPU and memory also.) 
You may be able to find a more recent, complete, used computer for a decent price on ebay, newegg, or amazon, example: [https://www.amazon.com/Dell-Optiplex-990-SFF-Desktop/dp/B01HTVADHW/ref=sr_1_7?crid=26S6JVK4S8MDZ&keywords=used+desktop+computer&qid=1579481118&s=pc&sprefix=used%2Caps%2C162&sr=1-7]("https://www.amazon.com/Dell-Optiplex-990-SFF-Desktop/dp/B01HTVADHW/ref=sr_1_7?crid=26S6JVK4S8MDZ&keywords=used+desktop+computer&qid=1579481118&s=pc&sprefix=used%2Caps%2C162&sr=1-7")
Your current system will still run one of the *buntu flavors.

---

### Post by crackers_altitude on 2020-01-20
thank you! This program is awesome!

the machine has an Acer WMCP78M. Sadly, Acer does not have an obvious page for it. There are some moderately interesting pages which can be found with a search, however, it is pointing to - again, without clear reason - of a hard limit of 4 GB memory for this motherboard, and thus, for an Aspire AX1300.

learned something here - I thought the memory limit of any machine was based on how many chips were on the RAM DIMMs - not something in the motherboard.

---

### Post by crackers_altitude on 2020-01-20
we carry on.

perhaps one day, a new-to-me computer - it is quite tempting, at that price.

---

### Post by CatKiller on 2020-01-20
> **crackers_altitude said:**
> 
learned something here - I thought the memory limit of any machine was based on how many chips were on the RAM DIMMs - not something in the motherboard.

Nope. The memory controller needs to be able to address every cell of the RAM for it to work. Bigger chips, more chips, double-sided modules, are all addressed differently. If the memory controller doesn't know how to address those cells then they can't be used.

Back in the day the memory controller was part of the northbridge on the motherboard. These days it's integrated into the CPU.

---

### Post by Autodave on 2020-01-20
Every computer is limited.  Some are quite high, but they are still limited.

---

### Post by Yellow Pasque on 2020-01-21
> **CatKiller said:**
> Back in the day the memory controller was part of the northbridge on the motherboard. These days it's integrated into the CPU.

That has nothing to do with it. It's a Socket AM2(+), so the memory controller is integrated into the CPU. The CPU and memory controller are capable of 64-bit goodness. It's the BIOS that limits it to 4GB. Why? Because that makes it easier when working with PCI address space. This machine came with Windows Vista Home Premium (32-bit) at a time when 64-bit Windows OS's were an oddity for power users and the masses stuck with WinXP 32 bit for driver compatibility.

---

### Post by crackers_altitude on 2020-01-22
> **Yellow Pasque said:**
>  It's the BIOS that limits it to 4GB. Why? Because that makes it easier when working with PCI address space. This machine came with Windows Vista Home Premium (32-bit) at a time when 64-bit Windows OS's were an oddity for power users and the masses stuck with WinXP 32 bit for driver compatibility.

that's interesting - yes indeed, before I was the owner, it had Windows on it.

so... well... what about updating the BIOS? Or is your argument that there is something special about PCI address space itself, ... vis-a-vis... 4 GB maximum RAM?

---

