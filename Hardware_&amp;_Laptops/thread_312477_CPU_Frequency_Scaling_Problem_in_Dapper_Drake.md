---
title: "CPU Frequency Scaling Problem in Dapper Drake"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by haxality on 2006-12-04
This is partly a question and partly a problem. I have tried searching and IRC and have yet to figure out what is going on with my CPU. Basically, I have powernowd installed and it automatically runs at boot. When I check my CPU speed, it always shows up as the lowest setting. Is this because my system needs to be under load? In any case, I decided I would rather manually choose the frequency. So I uninstalled powernowd, but now I get the error "no cpufreq support" when I try to use cpufreq-selector. Someone, please help! I am open to just about any option as long as I can prolong my battery life AND still be able to use all my CPU's power when I want it.


EDIT: Nevermind, it turns out my system was just usually under the required 80% CPU load. Leaving this thread as a reference for anyone else who is unsure if powernowd is working.

---

### Post by drphilngood on 2006-12-04
If you like, you can reconfigure the cpu frequency applet to allow you to manually adjust cpu scaling.  This thread shows you how:

[cpufreq scaling applet: manual scaling]("http://ubuntuforums.org/showthread.php?t=214007")

Cheers!

---

### Post by haxality on 2006-12-05
thanks!

---

### Post by drphilngood on 2006-12-06
You´re welcome; good to see it worked out for you.

---

