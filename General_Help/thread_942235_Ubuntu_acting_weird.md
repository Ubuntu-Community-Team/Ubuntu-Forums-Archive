---
title: "Ubuntu acting weird"
date: 2008-10-09
forum: General Help
---

### Post by AndreiMe on 2008-10-09
so i have this problem. i boot ubuntu start conky and it shows me ubuntu is currently using 530~550 mega ram out of 1 giga. this is without anything started. i just reinsalled the system and followed a tutorial from linux.com [http://www.linux.com/feature/149040](http://www.linux.com/feature/149040) , read adoub that program installed it myself and worked like a charm with very few ram for about two days. i don't think it's from that. this is weird because my windows xp with kaspersky av , extensis suitcase loaded with about 600 fonts, windows search bar, magic iso, winamp and opera with 12 tabs open and still i have 511200 (at the exact second), roughly about 510 mega ram free. please help anyone?

---

### Post by Bakon Jarser on 2008-10-09
use the system monitor or top to find out what is using all your ram.

System > Administration > System Monitor

```
top
```

---

### Post by cariboo on 2008-10-09
There is nothing wrong with your installation, Linux uses memory differently from Windows.

> From the Gentoo Memory Management FAQ
Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

The biggest place it's being used is in the disk cache, which is currently over 290 MB. This is reported by top as "cached". Cached memory is essentially free, in that it can be replaced quickly if a running (or newly starting) program needs the memory.

The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from there is around 1,000 times quicker than getting it from the hard disk. If it's not found in the cache, the hard disk needs to be read anyway, but in that case nothing has been lost in time. 

Hope this helps.

Jim

---

### Post by IcemanV9 on 2008-10-09
In the terminal ...
```
free -m
```
look at "-/+ buffers/cache:" line and under "free" column. See, you have a plenty of free memory. As someone already mentioned that Linux just manages the memory differently than Windows does. That's all.

---

