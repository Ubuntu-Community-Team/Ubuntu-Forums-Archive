---
title: "what should I upgrade?"
date: 2008-09-26
forum: Hardware
---

### Post by ipburbank on 2008-09-26
I'm an avid 3D modeler, and I make many animations that take days to make a test animation at a low res. before I send it off to the render farm (plug for burp.boinc.dk !!!). I have a quad core, running at 3.6 ghz, a geforce 9600, and abit ip35 pro motherboard. I'm wondering what I should do to give my system a boost, but I'm in middle school, no job, so more power and less $ is best. I'm wondering if there is a program that will show me what the slowest part of my system is (both the cpu and gpu are pinned as fast as i can tell, i don't have a gpu meter (if you can lead me to one that would be great) but when i move windows they leave trails. Some things I'm thinking of: another graphics card, using SLI (what would you recommend? I would like really fast, prob. 2 processors if it is cheap enough) or a faster CPU, and coolest would be a two-CPU motherboard (ok, if anyone can find a cheap one of these, many thanks!!!).

So basically I'm looking for software to find the bottleneck, and advice.

~thanks in advance, Istvan.

---

### Post by SuperSonic4 on 2008-09-26
Cooling would probably be cheapest :bleh:. With extra cooling you can overclock your pc getting more out if it if you have the expertise.

---

### Post by hansdown on 2008-09-26
Hi ipburbank.

System monitor will give you some insight into what's happening with your system.

You can find it in synaptic.

---

### Post by Crafty Kisses on 2008-09-26
Use gkrellm and as stated above cooling should be fairly cheap.

---

### Post by ipburbank on 2008-09-27
thanks guys, I actually have my system OC'd, my q-core running over a GHZ faster than the box said, and on a warm day it gets into the 70 degree range, but not up to 80 (my personal comfort limit) (I can't OC any more, if I do I start having stability issues). So as cooling goes I think I'm fine, the big problem is GPU monitoring. I can see the cpu, and system load monitors, but not my GPU load. The other thing is RAM, I am often filling my ram, and most of my swap (I might add another swap file, but still ram would be nice) however ram doesn't quite fit the cheap for power thing. I had a thread about GPU monitoring, but nobody could tell me how to do that... If there is a program though, I would love to hear about it!

---

### Post by emshains on 2008-09-27
Get nvclock!

```
sudo apt-get install nvclock nvclock-gtk
```

---

### Post by Sef on 2008-09-27
How much ram do you have?

---

### Post by ipburbank on 2008-09-27
I have 4GB, but for larger projects in blender (3d modeling suit) i fill it right up. Right now my ram is all gone, plus 3/4 of my swap. Has anyone noticed blender doesn't release ram all the time? I just downloaded and installed that GPU overclocker, but I would still like to see where the jam is, the cpu or gpu, or ram...

---

### Post by ipburbank on 2008-09-27
I don't have the whole system load figured out, but if my system monitor is less than 100% while rendering (cpu is pinned) then what does that mean? does that mean that the GPU or something else has some idle time?

---

