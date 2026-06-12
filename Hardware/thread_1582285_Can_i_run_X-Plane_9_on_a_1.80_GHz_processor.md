---
title: "Can i run X-Plane 9 on a 1.80 GHz processor"
date: 2010-09-26
forum: Hardware
---

### Post by Wakawakamush on 2010-09-26
Hi guys,

I saw [here]("http://www.x-plane.com/pg_Sys_reqs.html") that i will need a 2 GHz processor for x-plane, but i thought that i was maybe possible on an 1.80 cpu when i am using it with linux.

so, what do you say?

(sorry for my extremely bad english)

---

### Post by cascade9 on 2010-09-26
Your english is fine ;) 

Its possible. 

When software says 'need 2GHz or faster' they normally mean the slowest 2GHz CPU (like a celeron 2.0GHz). So if you've got a good 1.8GHz then it would be faster than a 'bad' 2.0GHz (eg- I had 2 different 1.8GHz AMD athlons, a 2200+ and a 2500+. Both of which were a lot faster than a Celeron 2.0Ghz, or evena  P4 2.0GHz) 

GHz is a bad way to measure system performance anyway.

---

### Post by Fafler on 2010-09-26
Having a fast graphics card can for some part make up for the slower CPU. And as Cascade9 said, ghz is in no way a measurement for performance.

[http://wiki.x-plane.com/What_Hardware_to_Buy](http://wiki.x-plane.com/What_Hardware_to_Buy)

Looking at the above link, it also tells you need a video card with at least 32 mb memory. Even low even low end video cards have had more than that for for quite some years now, so theres a good chance they mean a older P4 based processor.

Anyway, to tell us exactly what hardware you have, open a terminal and type the following:

```
cat /proc/cpuinfo | grep name
lspci | grep VGA
free
```

Cut'n'paste the results here.

---

### Post by Wakawakamush on 2010-09-26
jorn@jorn-desktop:~$ cat /proc/cpuinfo | grep name
model name	: Intel(R) Pentium(R) 4 CPU 1.80GHz
jorn@jorn-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
jorn@jorn-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        509308     494736      14572          0      31192     181400
-/+ buffers/cache:     282144     227164
Swap:       939760       4312     935448

that are the results, but i am going to buy more ram to get 1 gb and i am going to buy a 128 mb graphics card

---

### Post by Fafler on 2010-09-26
You could very cheaply upgrade the PC. And your CPU is actually the prime example of how little work a CPU can be able to do on a certain clock. I'll bet your system won't be fasyt enough to run X Plane without frameloss/stuttering.

---

### Post by Wakawakamush on 2010-09-26
so you say i should buy a new cpu?

---

### Post by Fafler on 2010-09-26
If your system supports it. But if you can afford it, you really should look into upgrading CPU, motherboard and RAM.

The CPU you have now is either socket 423 or socket 478 and it uses a 400 mt/s bus. If it's socket 423, you can't upgrade beyond 2.0 ghz and it's not really worth upgrading it at all. If it's socket 478, you can upgrade to 3.0 or 3.4 ghz, depending on your chipset. But you need to make sure your chipset supports the higher FSB some of the faster P4 chips use. To identify your chipset, please post the complete output of lspci.

What you really should do is get a LGA775 board with a Core 2 Duo and 2 gb DDR2 RAM. I've brought several systems like that in the last year at around $60 second hand. Also get a newer Nvidia card and you're flying ;-) A Core 2 Duo at 2.0 ghz will be around twice as fast as your current one, depending on the type of workload.

---

### Post by Wakawakamush on 2010-09-26
I think that is going to be a bit expensive for me...

i gues i wil stay with playing x-plane on mijn itouch for now.

---

