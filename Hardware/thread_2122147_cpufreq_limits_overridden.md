---
title: "cpufreq limits overridden?"
date: 2013-03-04
forum: Hardware
---

### Post by Vermind on 2013-03-04
Hi,
I have an Asus UX31 ultrabook with a core i7 4-core processor, running Ubuntu 12.04.
It overheats when playing Zero-K ( [http://zero-k.info/](http://zero-k.info/) , a Spring engine game ). The overheat causes an immediate shutdown if I do not stop the game before that.
I am trying to workaround the overheat by setting cpufreq limits like this:

[FONT=Courier New]cpufreq-set -r --max 1.20GHz -g ondemand[/FONT]

The 1.2 GHz limit holds for some 5-10 minutes when starting the game, but after that the 4 cores just go up to 1.8 GHz without permission. I can see this with

[FONT=Courier New]sudo cpufreq-info  | grep current[/FONT]

The (asserted by call to hardware) numbers climb to 1.8 GHz while the limits stay the same. Also, without sudo I only get values within the limits, since the user cannot query the hardware.

Any idea how I can keep the CPU from going above the cpufreq limits or workaround the overheat in another way?

P.S. I am using this GNOME Shell extension to see that the CPU overheats: [https://github.com/xtranophilist/gnome-shell-extension-cpu-temperature](https://github.com/xtranophilist/gnome-shell-extension-cpu-temperature)

Thanks,

---

