---
title: "Speedstep problems"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by madchicken on 2006-06-26
Hi to all.
After the upgrade to Dapper my speedstep stopped to work. I manually added all modules for speedstep to my kernel (2.6.15-25-686) to get it work again for my laptop (Sony Vaio PCG-K195HP).
But now I have a problem: my processor steps only between 74%, 87% and 100%, so when I'm on battery running at 74% I only have 1 hour and a quarter of power.
Is there anyone that knows if it is possible to configure the steps of the processor?
My processor is a genuine Intel Pentium 4.

Thank you very much.

---

### Post by madchicken on 2006-07-09
Hi guys. I still have no solution for this problem. Could anyone help me?
I found that on my laptop I can only load 2 modules for the speedstep: the first one is p4_clockmod that only gives me steps over 2Ghz, and the second one is acpi-cpufreq that only give me the lowest step of 1.6Ghz and the highest step of 2.8Ghz. Currently I'm running the second one, so with battery plugged I can go at 1.6Ghz. 
If I try to load speedstep_ich (that I think is the right module for me) I get a "No such device" error.

I still can't understand why my CPU supports 9 steps and I can use only 2 of them.
Any help is very appreciated.

Regards,
Pierpaolo

---

### Post by Hellkeepa on 2006-07-10
HELLo!

Your problem sounds a bit like some of the side effects I encountered from a bug in the -686 kernel. So I was wondering if you've read the following thread, and the one I've linked to there?
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Hopefully it'll be of some help for you, if this is indeed the same bug that's causing the issues.

Happy codin'!

---

### Post by madchicken on 2006-07-11
Thank you Hellkeepa. I don't think the two problem are related. I don't have problem with load of my cpu and over heating, but only problem with modules for handling speedstep. I'll try with the -386 kernel to see if the problem is due to the SMP compilation.

---

### Post by fast1 on 2006-07-11
Doesn't Intel's Speedstep provide only two modes: "Maximum Performance Mode" and "Battery Mode"?

---

### Post by madchicken on 2006-07-11
Uh...this is good question. But if so, why with Breezy I had more steps?
And why using p4_clockmod module I get 3 steps only above 2Ghz?

---

### Post by xrchris on 2006-07-11
So does your notebook have an Intel P4 desktop processor or an Intel P-M processor?

---

### Post by fast1 on 2006-07-11
Aren't those percentages the throttling states?
If they are the throttling states, you can modify them by setting
/proc/acpi/processor/CPU0/limit

Actually, I'm not an expert at all. I just read something on speedstep around. In particular, look at
[http://acpi.sourceforge.net/documentation/processor.html](http://acpi.sourceforge.net/documentation/processor.html)

---

