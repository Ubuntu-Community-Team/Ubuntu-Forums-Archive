---
title: "Unlocking cores - old topic but I am new, please advice"
date: 2012-08-28
forum: Hardware
---

### Post by cannon_dt on 2012-08-28
Hi,

I have the foll combination on my rig:
1. Motherboard: ASUS M4A785TD-V EVO AM3 AMD 785G HDMI ATX AMD
2. CPU: AMD Phenom II X2 550 Black Edition

After reading up on the internet I was curious to see if I could unlock the 2 other cores. So I was able to set the ACC to auto, enable unleashing mode and set 4 cores usage. Once I did this the system automatically rebooted, did a disk check and it logged in fine into my 11.10 Ubuntu.

Now what should I do? I am a little concerned as I am not sure about the repercussions if I continue like this. What stress testing should I do given that it is Ubuntu? What else should I check for? Should I now try to overclock? I am feeling a little lost even though I was able to unlock the cores (cpu-g reported 4 cores after my BIOS tweak).

Please advice as to what my next steps should be. 

Thanks,
Canon

---

### Post by Dr.Paneas on 2012-09-05
These extra cores are intentionally disabled by AMD because of their strange/faulty behavior. You have to manually identify which core issues the post problem and leave it disabled (setting affinity on each CPU separately while running a bench). Eventually most people go with 3-cores. If your system isn't able to boot, there is nothing you can do. So adjusting VCore or other voltages no matter in this.

Note that the more cores you have enabled the harder overclocking gets.

---

### Post by cannon_dt on 2012-09-05
I understand, I will check and see how many cores can actually get enabled and be stable.
One question however - in your last statement - the more cores you enable, harder overclocking gets - is that w.r.t. to the temps increase due to more cores running? Or is there something else you are referring to here?

Thanks,
Ananth

---

