---
title: "Acer Travelmate 4502LCi no CPU regulation"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by Fullofit on 2006-07-07
I recently installed breezy on my Acer Travelmate 4502LCi and find that the battery discharges very quickly, the computer gets too hot and the fan does not cut in whilst being logged in.
I gather that this is a CPU frequency problem (ie it is not recognised) and that I will have to hack the kernel. This is the first time that I have worked with Linux and do not know where to begin.

---

### Post by Fullofit on 2006-07-08
Assuming that most travelmates and/or centrinos are similar I look around and  found the text

After a search on the ubuntu forums it seemed that i had to insert more modules into the kernel, and that since 2.6.12-10. Since i’m not into recompiling kernels myself i was happy to find the following commands suggestion:

modprobe speedstep-lib
modprobe p4-clockmod
modprobe freq-table
powernowd

Searching for those modules on my system i found them under ‘/lib/kernel/2.6.12-10-386/kernel/arch/i386/kernel/cpu/cpufreq/’, together with the interesting module speedstep-centrino. After trying the following steps i got my cpu scaling up and running:

modprobe speedstep-lib
modprobe speedstep-centrino
powernowd

After these commands you’ll probably have to re-add the frequency monitor applet to the bar. To make these changes permanent you’ll have to add the previous 3 commands to your /etc/modules file. Good luck! 

except the last paragraph, it all went well. The problem is how do I edit /etc/modules and why does my computer still run so hot?

---

