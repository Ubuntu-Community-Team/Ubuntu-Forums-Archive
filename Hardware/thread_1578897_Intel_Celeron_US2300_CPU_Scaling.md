---
title: "Intel Celeron US2300 CPU Scaling"
date: 2010-09-21
forum: Hardware
---

### Post by jimmyxx on 2010-09-21
Hi I've recently got a UL20A which has a dual-core 1.2Ghz SU2300 processor. Specification of the processor: [http://ark.intel.com/Product.aspx?id=42779]("http://ark.intel.com/Product.aspx?id=42779")

I'm trying to enable CPU scaling however when I add the gnome applet it says 'CPU frequency scaling unsupported'. I've installed cpufrequtils & sysfsutils packages from repo. When I try to run:
> sudo modprobe p4_clockmod

I get the following error:
> FATAL: Error inserting p4_clockmod (/lib/modules/2.6.32-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

I've read online that this could suggest my CPU doesn't support scaling - however I believe windows 7 64bit acomplishes it with it's asus battery saving mode etc? Another site I read suggests I could be running the wrong kernel?

My kernel version:
> Linux jimmypad 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux 

I've attached CPU info output to the post. Any advice would be great.

Thanks!

---

### Post by jimmyxx on 2010-09-23
Title should read SU2300

(bump ;))

---

