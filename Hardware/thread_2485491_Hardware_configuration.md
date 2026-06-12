---
title: "Hardware configuration"
date: 2023-03-31
forum: Hardware
---

### Post by sundaresh on 2023-03-31
I would like to know what, slightly future proof, reasonably priced, motherboard, processor, ram configuration is best for loading latest ubuntu, computer use largely for programming purposes. Is intel or is amd the better choice ?

---

### Post by TheFu on 2023-03-31
"Better" is highly subjective.
"Reasonably priced" is highly subjective.
"Future proof" is impossible, but ...

by getting 12+ month old hardware that is from the most popular named vendors, you can avoid many issues.

The needs of a perl programmer are vastly different from the needs of a Java developer.  The type of programming and the languages selected will matter too.

Intel has more security problems, historically, than AMD.  You didn't mention that.  You also didn't mention any required performance, whether a desktop, laptop, miniPC was desired.  You didn't mention how important sensor data (system temperatures) is either.  AMD is just getting sensor hooks in the most recent kernels.  Intel tends to get sensor hooks much faster. OTOH, if the system is properly cooled (which doesn't take much), then sensor data isn't too important.

So, Lacking **any** real information, price being no object, assuming the computer is a desktop, and running in a climate controlled room with 35% humidity, I'd say to get 
* Intel Core i7 12-gen CPU (don't go newer)
* Asus Motherboard with the RAM, SSD, SATA, and intel NICs you want
* 64G-128G of RAM (for perl, this is 10x too much, but you didn't say), for Java, it won't be enough.
* AMD GPU ... or use the iGPU from the Intel CPU.

Personally, I'm an AMD Ryzen lover, but Intel has become price/performance competitive and there's little doubt that Intel is slightly better supported than AMD CPUs.  OTOH, I love my Ryzen 5 5600G systems.  20K passmarks for $120, and it included a capable GPU in that price.  I doubt that APU is still available at that price. I haven't looked recently.  AM4 platform for Ryzen has just ended.  AM5 is what the new AMD Ryzen 7xxx series CPUs are using. That forces a change to more expensive DDR4 RAM.  With AM4, DDR4 RAM works.  The 2% performance gain isn't worth 2x the cost to me.

I have a DDR3 system from 2010 still running here too. It does what it needs to do, just fine. It doesn't have any SSD storage at all.

Asus makes the best motherboards with MSI a close second.  Avoid Realtek NICs. Stick with Intel for the no-hassle, high-performance NICs.  You'll probably get a 2.5Gbps Intel NIC these days.

When it comes to storage, I'm partial to Samsung NVMe SSDs.  I'd go with the "PRO" series, if the 20% cost premium isn't an issue.

Oh, and if you plan to upgrade the CPU over the next few years as newer CPUs become available, then I'd NOT get Intel and I'd go with a AM5 Ryzen.  That makes the CPU upgrade just 1 component, nothing else.  The AM4 socket line lasted 7+ yrs. That's 7 yrs of CPU upgrades that nearly all work in the same motherboard from $80-$600 Ryzen CPUs with an amazing spread of available performance.  Intel seems to change their sockets every 18 months, so a new motherboard will be required for almost any CPU upgrade.  But if you buy and never upgrade, then having a long-lived socket like AM5 will be, isn't important.

So, which is "better"?  That depends.

---

### Post by sundaresh on 2023-04-01
So intel earlier generation like 3rd , 4th 5th and 6th are not worth it. Will ubuntu not work on any of these. What about on amd ?

---

### Post by TheFu on 2023-04-01
> **sundaresh said:**
> So intel earlier generation like 3rd , 4th 5th and 6th are not worth it. Will ubuntu not work on any of these. What about on amd ?

All of those have unpatched Intel security faults that were well published.  [https://www.techradar.com/news/intel-has-discovered-a-load-of-more-serious-firmware-vulnerabilities](https://www.techradar.com/news/intel-has-discovered-a-load-of-more-serious-firmware-vulnerabilities)  Older CPUs have more.  Intel doesn't look into EOL CPUs for faults.

A Core i3 from today is about as fast as a Core i7 from 6 yrs ago.  The best way to compare CPU speeds/performance is to look up the "passmark" value for each CPU.  Those change every year, so comparisons need to be made using the same passmark DB version.  In 2012, I had a Celeron with 1500 passmarks that worked fine.  That same Celeron is listed at 600 passmarks today. That's because newer CPUs have so much more capability that the passmark tests have to change to stress them more.

But it is your system. I wouldn't get any Intel older than 9th-gen.  8th-gen is from 2017-ish, so already 6 yrs old.

If you answer some of the questions asked, you'll get better suggestions that fit your needs.

---

