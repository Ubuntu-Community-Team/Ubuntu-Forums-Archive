---
title: "Heat Issues with Ubuntu"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by wipeout140 on 2007-03-10
After downloading Ubuntu Ultimate Edition 1.2 ISO and booting it up i liked it with all the software pre-installed i wanted, all updated and wireless ready. i installed it to my laptop and got it dual booting with windows XP Home, enjoy ubuntu massively i would swap from XP to Linux straight away but two issues hold me back

[LIST=1]
[*]Battery Life is not as long on Linux as Windows (I can live with it)
[*]It gets a lot hotter in Linux then windows. after 45 minutes its hotter if have windows running for day (Main reason i am holding back)
[/LIST]

If you can help me resolve this issues. Next time i will posting on Linux not Windows

---

### Post by bernied on 2007-03-10
I suspect that your laptop is simply running flat out, with no cpu frequency scaling. Have a look at the output of this:
```
cat /proc/cpuinfo
```
Is there a number bigger than 1 next to 'stepping :'? This means you can make your cpu run at different speeds. What speed is it running at right now? This is labelled as 'cpu MHz :'

I think the most common solution is cpufrequtils and cpufreqd. There is also powernowd. You may already have one or more of these installed. I think though that each is specific to a processor family - I mean one is for AMD and one is for Intel (I think). Anyway, google these with ubuntu and see what you can find. They are definitely standard for ubuntu so you will find them in the normal repositories - just use your package manager to install.

---

### Post by bernied on 2007-03-10
[This](http://doc.gwos.org/index.php/CPUFreq) might be useful. I use cpufreq on a Dell D610 which has a 2.1GHz Pentium M processor.

---

### Post by wipeout140 on 2007-03-10
Thanks for post. but thing is it runs Windows XP Perfectly and even Windows Vista when i was testing RC1 and RC2. So i hardly doubt its CPU running flatout as only uses 2% on windows XP

My Specs anyway:

AMD 64 3200+
1024mb
ATI 9700

Its just fan does not work as in windows. So its a Linux Incompatible

Would say i know quite abit of computer built a few computers and sold one but still haves me stumped

---

### Post by bernied on 2007-03-10
Ahem - I was referring to CPU frequency scaling, not CPU usage. I'm not suggesting that ubuntu is using 100% of the CPU all of the time, just that it is failing to scale down the frequency when the CPU is not being used. This is easy to check, even for someone who knows quite a bit about Windows (in my experience that is often a disadvantage when working with linux).

[Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)

---

