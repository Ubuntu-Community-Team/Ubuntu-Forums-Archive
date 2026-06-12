---
title: "Intel Core2 Duo T5800 and 3GB RAM, should I install 64 bits?"
date: 2012-10-25
forum: Hardware
---

### Post by COMECON on 2012-10-25
Hi!
I have an Acer Aspire 6930, with 3GB RAM and a NVIDIA GeForce 9300M GS. The processor is an Intel Core2 Duo T5800 @ 2GHz, and I also installed 32 bit versions of all. But, watching at /proc/cpuinfo I saw it has the **lm** flag, which I think is related to 64 bit. Look:
```

comecon@quantal:~$ cat /proc/cpuinfo  | grep lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm

```
Also, looking at Intel's site I saw it's a 64 bit processor. So, should I install the 64 bit Ubuntu?
Thankyou!

---

### Post by oldfred on 2012-10-25
Welcome to the forums.

All Core Duo are 64 bit, no reason not to use 64 bit.

My laptop Core Duo only has 1.5GB of RAM so it is a bit light with 64bit but runs mostly ok. Very occasionally I get a bit of swap going on and swap is slow.  I try not to load too many things at once. But I use 64 bit so I have the same version as my Desktop.

---

### Post by ahallubuntu on 2012-10-25
Stick with the 32 bit OS unless you plan to upgrade to 4GB - then you might see a tiny bit more RAM with the 64 bit version.  Otherwise, don't expect much if any performance benefit with a 64 bit OS.  There are some other benefits besides ability to address more than 4GB (you can have larger processes), but most likely you'll never notice.  64 bit processes can actually be a bit less efficient in some cases.

---

### Post by ahallubuntu on 2012-10-25
> **oldfred said:**
> Welcome to the forums.

All Core Duo are 64 bit, no reason not to use 64 bit.

To be clear: there are two different Intel CPU lines: the "Core Duo" (that came out earlier) and "Core 2 Duo" that was sold longer.

"Core Duo" are all 32 bit as I understand it.  At least, the ones in my couple of Dell laptops were 32 bit only.

"Core 2 Duo" are all 64 bit as I understand it.

If in doubt, look up the CPU number in Google and find out whether it is 64 bit capable.  (The T5800 is 64 bit for sure.)  A 32 bit OS will of course work with either a 32 bit or 64 bit CPU.

---

### Post by COMECON on 2012-10-26
So, then, it's better to stay with 32 bit or upgrade to 64 bit? As I change my distribution... each week (I know I'm very crazy) it'd be fine to check how do the 64 bit work!
But, I remember, I installed Fedora 17 64 bit by mistake and I had problems... but when I installed 32 bit I didn't have them.
Thanks!!!

---

### Post by ahallubuntu on 2012-10-26
I doubt you'd have any problems with the 64 bit version of Ubuntu on your hardware.  I'm just saying, it's probably not going to be any faster and even be slightly slower in some cases (doubt you would notice either way).  The biggest benefit of 64 bit would come if you upgraded to 4GB of RAM or more.  If you have no plans to upgrade beyond 3GB, stick with the 32 bit OS.

---

### Post by oldfred on 2012-10-26
This has a nice list of Intel processors. Even back to 4bit and thru current. Although I remember some were 32/16 internal/external - 80286 or classed as 16bit.

[http://en.wikipedia.org/wiki/List_of_Intel_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors)

---

