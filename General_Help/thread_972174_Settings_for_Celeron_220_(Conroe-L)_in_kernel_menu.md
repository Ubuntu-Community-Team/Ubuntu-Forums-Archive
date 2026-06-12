---
title: "Settings for Celeron 220 (Conroe-L) in kernel menuconfig"
date: 2008-11-05
forum: General Help
---

### Post by romnatiw on 2008-11-05
Hi.

I have dedicated server with Intel Celeron 220 (Conroe-L). How should I set settings for this CPU in vanilla 2.6 x64 kernel in menuconfig? Should I enable SMP and MPS Table? AFAIK, this is needed when processor has more than one core, there is two or more processors or CPU supports HyperThreading. Celeron 220 has one core, but I don't know what's with HyperThreading. At this moment I have this disabled, but maybe I should change this?

Second question is about CPU family in menuconfig. I can choose between "Opteron/Athlon64/Hammer/K8", "Intel P4 / older Netburst based Xeon", "Core 2/newer Xeon" and "Generic-x86-64". Default is Generic-x86-64. Should I change this for a better performance? AFAIK, Celeron 220 (Conroe-L) is based on Core microarchitecture, so maybe should I use "Core 2/newer Xeon"? I don't know so I asking for help.

---

### Post by cariboo on 2008-11-05
Is there a particular reason why you want to compile a custom kernel, or are you just doing it for fun?

If you are dong it to learn something, try the different options and see what happens.

Check here for more info on your cpu:

[http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors)

Jim

---

### Post by romnatiw on 2008-11-05
I want to have newest kernel and implement grsecurity with PaX to increase security. By the way I want to optimize kernel settings to increase performance. I tried SMP on and off and server works without problems in both instances. I heard that if SMP is not needed (singe core processor without HT technology), then it should be off, but I don't know what should I set in this case. What you recommend? Maybe should I benchmark CPU performance with some application? I need help. ;) Sorry for my english.

---

### Post by romnatiw on 2008-11-06
So? ;)

---

