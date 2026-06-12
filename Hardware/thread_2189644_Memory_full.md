---
title: "Memory full"
date: 2013-11-23
forum: Hardware
---

### Post by SimpsonTruckDriver on 2013-11-23
I could not find the EXACT reason or fix for this online, so I thought I would ask a new question. Over the last week, my Dell Inspiron E1505 with 2Gb RAM and Ubuntu 12.04 LTS (Unity Desktop) has slowed down significantly. When I go into the TERMINAL, I would type:

tsimpson@laptop:~$ top

And aside from all the processes, I found this:

Mem:   2064040k total, 1843004k used, 221036k free
Swap:  4882428k total, 17944k used, 4864484k free

The only programs I have running, other than Wi-Fi, is Firefox 25.1, XScreensaver  5.15, and Thunderbird 24.1. I found a way online to basically clear out the RAM, which worked, but was only temporary. What could be the issue and fix?

Thanks
Todd S

---

### Post by nosmadar on 2013-11-23
I'm not sure that Memory per se, is your problem.  
plase look at this link:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

If you the System Monitor utiltiy, what does it show for CPU consumption?
Can you quantify what you mean by "Slow"?   
-- what kinds of things are you doing and how much longer does it take to do them?

---

### Post by SimpsonTruckDriver on 2013-11-23
Now that I think about it, it might just be time-hog (and now memory-hog) Facebook. Using System Monitor, Memory shows 48% taken, Swap is 0.5% taken. When I meant "slow", I would type a sentence, but it wouldn't show in FB for a few seconds. I guess it was not really knowing what TOP meant, and using System Monitor showed that it is actually OK.

TS

---

### Post by sanderj on 2013-11-24
> **SimpsonTruckDriver said:**
> Now that I think about it, it might just be time-hog (and now memory-hog) Facebook. Using System Monitor, Memory shows 48% taken, Swap is 0.5% taken. When I meant "slow", I would type a sentence, but it wouldn't show in FB for a few seconds. I guess it was not really knowing what TOP meant, and using System Monitor showed that it is actually OK.

TS

OK, but you did understand what @nosmadar said? Linux does use your RAM ... no problem there.

Easy check for slownews: open a terminal and type:

```
uptime
top -bn1 | head -12
```

and post the output here.

---

### Post by grahammechanical on 2013-11-24
I think that top includes cache memory as part of used memory. Which it is in a certain sense. It does not mean that Ubuntu is a memory hog. 

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Regards.

---

