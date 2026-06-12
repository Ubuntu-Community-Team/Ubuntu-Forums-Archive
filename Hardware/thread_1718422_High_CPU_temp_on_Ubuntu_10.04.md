---
title: "High CPU temp on Ubuntu 10.04"
date: 2011-03-31
forum: Hardware
---

### Post by Jechem on 2011-03-31
Hi,

I have an AMD V120 processor and I've noticed that the temperature is higher in Ubuntu than what I get from Win7. I've reached temp of 73C on Ubuntu when playing flash video on google chrome while at idle state temp is around 53C-55C with 10-20% CPU use. Running is AWN, compiz, skype, screenlets. While on Win7 the highest I've encountered on the same flash video on google chrome is 65C and when idle the temp is 49C-52C with 20-30% CPU. Is Ubuntu bad at keeping my CPU cool? I haven't found any benchmark on the temp of the AMD V120 but I think above 70C is already alarming. If somebody can share their thoughts that would be great. Thanks.

---

### Post by TBABill on 2011-03-31
Above 70 is certainly alarming. Most machines start to protect themselves with thermal limits at 90-100C. Getting to 70 is concerning. Are you using Sun Java or openJDK? And Adobe Flash or Gnash?
 
It'd check everything from cpufreq throttling to vents and fan on the machine for obstructions. Make sure you have the right graphics driver installed (proprietary) and that the CPU is throttling properly with cpufreq (I like ondemand as my setting for cpufreq and that's the standard setting now in Linux distros I've used recently).

---

### Post by Yellow Pasque on 2011-03-31
Oh, and it's not a solution, but use Flash-aid extension to avoid Flash video, as watching video directly through the Flash plugin is very inefficient and uses a lot of CPU.

---

### Post by Jechem on 2011-03-31
Thanks for the replies.

> **TBABill said:**
> Above 70 is certainly alarming. Most machines start to protect themselves with thermal limits at 90-100C. Getting to 70 is concerning. Are you using Sun Java or openJDK? And Adobe Flash or Gnash?
 
It'd check everything from cpufreq throttling to vents and fan on the machine for obstructions. Make sure you have the right graphics driver installed (proprietary) and that the CPU is throttling properly with cpufreq (I like ondemand as my setting for cpufreq and that's the standard setting now in Linux distros I've used recently).

I'm using openJDK and Adobe Flash plugin right now. I just experienced 70C once but the average in Ubuntu is between 60-65C normal web browsing no flash running. My laptop is less than six months so I think it's still clean inside. Ondemand setting is as is I did not change it. Anyway, thanks for your inputs. I'll just have to observe the behavior more.

---

