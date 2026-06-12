---
title: "What is my hardware specifications?[Solved]"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by boxer1028 on 2007-10-05
My CPU is running a bit on the slow side with Ubuntu and I may need to install more RAM or upgrade a processor. I just want to know what my Processor and RAM specs are. I cant seem to find this info in Feisty 7.04. If this were XP all I would have to do is Right click on 'My Computer' and go to 'Properties' to get the info I need. How do you do this in Ubuntu?

---

### Post by louieb on 2007-10-05
My favorite way:
```
cat /proc/meminfo 
```
and
```
cat /proc/cpuinfo 
```

---

### Post by boxer1028 on 2007-10-08
thanks

---

