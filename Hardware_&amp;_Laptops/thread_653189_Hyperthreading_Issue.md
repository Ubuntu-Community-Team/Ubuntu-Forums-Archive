---
title: "Hyperthreading Issue"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by methodical on 2007-12-29
I just recently rebooted and was running the system monitor, and it is only displaying one cpu. Before the reboot though it was showing two cpus. For some reason it works sometimes and other times it doesn't. I have hyperthreading enabled in the BIOS.

What gives?

My processor is a Pentium 4 3.06GHz, and I'm running Ubuntu Gutsy 7.10.

Thanks...

---

### Post by LaRoza on 2007-12-29
That processor is a single core, I don't know exactly how HT is displayed, but it is not a dual core processor, so one CPU is all that you have.

Perhaps it displays as a dual core when hyper threading, but that is just a SWAG.

---

### Post by deanjm1963 on 2007-12-29
> **LaRoza said:**
> That processor is a single core, I don't know exactly how HT is displayed, but it is not a dual core processor, so one CPU is all that you have.

Perhaps it displays as a dual core when hyper threading, but that is just a SWAG.

It should appear as 2 processors, it might not have 2 physical cores but it has 2 virtual cores, I have the same processor on a desktop system.

I had similar problems a while back with 6.06 and 7.04, say every 6 or 7th reboot it would only appear as 1 processor, not 2. I checked my bios and found that the clock speed was not quite right, the cmos battery was on its way out, I changed it, made sure my clock settings and memory speed were correct and all has been great ever since.

Hope that helps...

---

### Post by methodical on 2007-12-29
> **deanjm1963 said:**
> It should appear as 2 processors, it might not have 2 physical cores but it has 2 virtual cores, I have the same processor on a desktop system.

I had similar problems a while back with 6.06 and 7.04, say every 6 or 7th reboot it would only appear as 1 processor, not 2. I checked my bios and found that the clock speed was not quite right, the cmos battery was on its way out, I changed it, made sure my clock settings and memory speed were correct and all has been great ever since.

Hope that helps...

Yes, that is how it is for me... It is every few reboots or so. How would I know what my clock settings/memory speed should be?

---

### Post by deanjm1963 on 2007-12-29
You should be able to check by entering your bios and checking your CPU clock settings

I just rebooted to check mine... 

CPU Host Frequency = 133 (hence 133 x 23 = 3059 (3.06Ghz)
AGP Host Frequency 33/66
Memory Frequency = 333

Don't assume they're the same for your PC, check out your motherboard/processor manuals first before making any adjustments.

---

### Post by methodical on 2007-12-29
Thanks I will check into it.

---

