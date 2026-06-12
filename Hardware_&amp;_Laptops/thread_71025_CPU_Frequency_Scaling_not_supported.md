---
title: "CPU Frequency Scaling not supported"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by mthaddon on 2005-10-02
Hi Folks,

I was trying to play around with the CPU scaling as I wanted to be able to set the CPU statically and then change back to dynamic. On a thread somewhere I saw someone recommending using cpufreqd instead of powernowd. I installed this, and then realized I didn't want that as by default it locked the CPU at 2GHz (my max) when on power (i.e. not battery), and this was getting noisy cos the fan kept kicking in.

I removed cpufreqd and now I can't seem to get back to the state I was at before and I get the message of the subject line whenever I log in, and there's definitely no CPU scaling going on.

Can anyone tell me how to get powernowd working again so that I'm back at the default setup?

Thanks, Tom

---

### Post by locutus42 on 2005-10-03
[QUOTE=mthaddon]Hi Folks,
I was trying to play around with the CPU scaling as I wanted to be able to set the CPU statically and then change back to dynamic. On a thread somewhere I saw someone recommending using cpufreqd instead of powernowd. I installed this, and then realized I didn't want that as by default it locked the CPU at 2GHz (my max) when on power (i.e. not battery), and this was getting noisy cos the fan kept kicking in.
I removed cpufreqd and now I can't seem to get back to the state I was at before and I get the message of the subject line whenever I log in, and there's definitely no CPU scaling going on.
Can anyone tell me how to get powernowd working again so that I'm back at the default setup?
Thanks, Tom[/QUOTE]
restart powernowd( sudo /etc/init.d/powernowd start ) or undo whatever you did to stop it from working. I just stop powernowd if I want to force the 100% CPU speed instead of the 50% speed powernowd throttles to on my machine.

---

### Post by GuyveR800 on 2005-10-03
This question has been answered numerous times already. Do you know there is a search function? ;)
Add "powernow-k8" to /etc/modules to get it working with AMD64 CPUs.

---

