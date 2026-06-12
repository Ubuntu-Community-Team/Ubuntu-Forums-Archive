---
title: "Minimum RAM for 12.04"
date: 2013-06-19
forum: Hardware
---

### Post by mayagrafix on 2013-06-19
Does different hardware need more or less RAM to run same version of Ubuntu?

I have 2 laptops with Ubuntu 12.04-2D. The "newer" one with a dual core processor at idle (no programs running) runs with 165 megs, whereas the "older" one with a single core CPU will not go below 225 megs. Swap use is at 0% on both. Both have same OS, with no extra start up programs added. They both run ok also. I'm just wondering if hardware requirements are different on older PC's.

Thanks for ur help.

---

### Post by snowpine on 2013-06-19
When you boot Ubuntu, it loads various modules into RAM that are required to support your individual hardware components. Because different computers have different builds, the RAM usage will vary depending on the size of the modules that are needed. RAM usage is actually a fairly meaningless statistic. Whether you are using 165mb vs. 225m is irrelevant to the actual performance. Actually, RAM can be used as cache to make the computer run *faster*! Generally, the only times you need to worry about RAM usage in Linux is if it's approaching 100% and/or if you are going into swap, which is slower than RAM.

Ubuntu recommends 512mb minimum according to: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

