---
title: "ridiculously bad performance, high cpu usage in Hardy"
date: 2008-07-11
forum: General Help
---

### Post by NoPantsJim on 2008-07-11
I'm running Hardy on a laptop with a Core 2 Duo at 1.8ghz and my performance is terrible. As I type this, the words are lagging behind how quickly I am typing.

When I open System Monitor and check Processes, the highest CPU usage is Firefox, which clocks in at 9%, then 5-6 other programs also taking single digit CPU usages. However, when I go to Resources to view the graphs, both of my cores are nearly maxed continuously.

Any ideas? I'm currently only running Firefox, Pidgin, compiz, and rythmbox.

---

### Post by sdennie on 2008-07-11
Is your machine fully updated?  Also, do not trust the output of the system monitor as, on an idle system, it will probably be taking the majority of the CPU.  It's a known and filed bug.

---

### Post by sonicb00m on 2008-07-11
You want a faster CPU, mate :D

Joking aside, make sure you are looking at all system process, not just the user one.

Have you got the file tracker indexing on? That can cause these kind of problems when it indexes a large drive.

---

### Post by bryncoles on 2008-07-11
and if you want an alternative to system monitor, since that gives inaccurate cpu usage readings, try opening a terminal and typing 'top'. then type '?' from within top to get a list of commands you can use.

---

### Post by mriedel on 2008-07-11
I had that identical problem on my Intel Pentium M / Centrino notebook. Extremely bad performance, though compiz and firefox competing for #1 in top at around 10% each at most. 

Nobody seemed to have an idea what it could be and I wanted encryption anyway, so I reinstalled form the alternate install CD and the performance issues were gone.

---

### Post by SpikeyMike on 2008-08-06
> **mriedel said:**
> I had that identical problem on my Intel Pentium M / Centrino notebook. Extremely bad performance, though compiz and firefox competing for #1 in top at around 10% each at most. 

Nobody seemed to have an idea what it could be and I wanted encryption anyway, so I reinstalled form the alternate install CD and the performance issues were gone.

my system is suffering from slow performance aswell, what is the alternate install CD? would like to try it

Spikey

---

