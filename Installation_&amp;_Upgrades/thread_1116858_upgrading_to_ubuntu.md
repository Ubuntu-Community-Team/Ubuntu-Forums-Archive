---
title: "upgrading to ubuntu"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by kevin36 on 2009-04-05
I asked on Friday I was asking about installing Ubuntu on a virus infested computer, and it completely resurrected the computer! Anyways, I've been playing around with Ubuntu all weekend, and I'm totally sold on it. I want to install it on a few more computers. My questions are, are any of the computers I'm going to install Ubuntu on capable of 64bit version? I'm sorry to ask such "n00bie" questions, but I need the help. The computers I'm going to install Ubuntu on are:

hp pavilion a645c
Memory: 434.4 MiB
Processor: AMD Athlon XP 3200+ (I think 2.2 Ghz)

acer aspire 5515
Memory: 2.7 GiB
Processor: AMD Athlon Processor 2650e (I think 1.6 Ghz)

Another question I have is how do I check my video card? I can't seem to figure it out on the Ubuntu desktop.

Finally, what function do you all set the function of your Windows button on your keyboard too? ;)

Thanks to all!!

---

### Post by AllenGG on 2009-04-05
First : good for you !
The AMD is a 64 bit processor.  the other appears to be a 32 bit.
Install the 32 bit version for most systems that you are NOT using. From experience there is sometimes a real lag in 64 bit drivers.
Next, the video card is easy, use the "system tools - Sysinfo" , which you can get with any live CD including Knoppix.

With friends computers I've installed linux Ubuntu, since some were having extreme virus and spyware problems.

---

### Post by kevin36 on 2009-04-05
Thanks for the help! But which AMD is the 64bit processor? Do you think both of the systems I posted should use 32bit Ubuntu? Finally, I still can't seem to find the video card... is in under the System tab on the Ubuntu desktop?

---

### Post by AllenGG on 2009-04-05
Ooops, sorry Kevin. I meant the first one.  AMD shows which processor does what on their support page. Intel does as well, it just takes longer.

---

### Post by AllenGG on 2009-04-05
Install "sysinfo" from Synaptic.  It will appear under "system tools in the applications menu.

---

### Post by ajgreeny on 2009-04-05
Also **hwinfo** from the repos will give you all the information on your hardware the same as ```
lshw
``` in terminal, but using a gui.

---

