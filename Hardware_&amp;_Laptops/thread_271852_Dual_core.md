---
title: "Dual core"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by Lster on 2006-10-05
I have an Intel Core Duo (1.66GHz, 2MB L2). Ubuntu seems very fast (faster than windows) but I am wondering if both cores are being used. Is there a way to check?

Thanks,
Lster

---

### Post by madmetal on 2006-10-05
in order to take advantage of both cores you must install and use the smp kernel(686-smp i think is better fo you)
smp uses multi-core/thread technology..

---

### Post by Lster on 2006-10-05
I cant find anything like SMP or 686 in Synaptic... What should I do next?

---

### Post by dphipps on 2006-10-05
What you want is linux-686-smp.  This package will install what you need.  You should be able to install it with this

```
sudo apt-get install linux-686-smp
```

---

### Post by Rhubarb on 2006-10-05
There's a generic linux 686 kernel meta-package you need to install via synaptic.  I can't remember the exact name of it as I'm at work at the moment (on windowzzzzz). There's a few threads here that'll tell you if you do a search (sorry I can't help you here at the moment).
If it says 686, it'll support your core duo.
If you want to know if it works, bring up the system monitor, if you see 2 cpus in the graph you know it's all working - it'll also be quite a bit faster too! :)

---

### Post by Lord Illidan on 2006-10-05
Aye, I love dual core!

---

### Post by John.Michael.Kane on 2006-10-05
1) Click on System
2) Click on Administration
3) Click Synaptic Package Manager
4) Click on search
5) In the search feild type linux-686 you should see an smp kernel.
6) Right click, and select Mark for installation

Make sure you have all the repositories enabled in your souces.list.

To see if both cores are seen 
```
dmesg | grep CPU
```

---

### Post by ruleboy on 2006-10-05
here is a great link on the topic

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

is you do a 'uname -a' and see somthing like the following, the SMP bit is the key, then you have both cores running.

Linux seven 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux


Mind you, dual cores only help if you have more than one app running hard, otherwise its no faster than a single core. I just upgraded to a DC at the same clock speed as my SC, its more responsive however no faster...unless you have an app designed to use two cores...

---

