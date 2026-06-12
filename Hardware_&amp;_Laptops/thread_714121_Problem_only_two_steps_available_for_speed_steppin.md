---
title: "Problem: only two steps available for speed stepping"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by broesch on 2008-03-03
Hi,

I recently installed Gutsy on an laptop running a Pentium M 2.00Ghz Dothan, which was running windows xp until then. It took me a while to realize but it seemed that the laptop was running hotter and louder then in windows. I investigated about cpu frequency scaling and found out what seems to be the problem, the minimum and maximum frequencies are correct (600,2000), but there are no steps in between, if i remember correctly there should be about 6 steps in between, in Windows I once used a program to configure the steps and i could configure about 8 steps.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
outputs 
2000000 600000

I tried to edit this file or echo to it as root but it says Access Denied

The gnome frequency applet only lets me choose among these two also.

i appreciate any help about the matter
Thanks

---

### Post by _Stevie_ on 2008-04-13
the problem is, that linux doesnt support more steps. the linux kernel reads the acpi values, thats why there are only 2 steps. whereas rmclock has much more steps. i'm not sure how rmclock does it. but i wish it was possible in linux too. in my case there
are only 3 steps instead of  6 in windows.

---

