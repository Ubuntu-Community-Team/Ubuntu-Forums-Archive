---
title: "How Much Space to Use for Swap"
date: 2015-10-25
forum: Hardware
---

### Post by cobalt2 on 2015-10-25
I have 4 GB of RAM installed. How much space is recommended for the swap?

---

### Post by mastablasta on 2015-10-25
4 GB if you plan to hibernate. you can use less maybe 2 GB just to have some. depends realyl on what you want doing. i have it on server and it didn't get used yet. you can also reduce the swapiness if you want - the time when the OS decides to use the /swap. it can use it when 50% ram s take or you can set it that it starts using it only when 90% is taken...

---

### Post by cobalt2 on 2015-10-25
What is the method for adjusting the RAM threshold for swap usage?

---

### Post by Bashing-om on 2015-10-25
cobalt2; Hello;

A good explanation:
[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

What you set it to is dependent on your use case . I find for my use case a setting of '10'  works just fine - 4 gigs of ram and a VERY small /swap partition .

[INDENT][INDENT]all in how you use it
[/INDENT][/INDENT]

---

### Post by cobalt2 on 2015-10-25
Hello Bashing-om. You have an interesting username. 'Bashing' as in using bash? Where does the 'om' come from? 

Do you have your swap partition mounted? 

By 10 you mean 10 GB?

---

### Post by Bashing-om on 2015-10-25
cobalt2; Hey ..

My system:
```

sysop@1404mini:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1197       2756         36         95        589
-/+ buffers/cache:        512       3441
Swap:            7          0          7
sysop@1404mini:~$

```

> 
Do you have your swap partition mounted? 

```

/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris

```
I multi-boot on this box, and my only  /swap partition is configured for all the installs to use this partition. 

As per the provided tutorial for setting a "swappiness" I have it set to 10 as the point to begin swapping out of ram to the /swap partition.
_____________-
As to my nick .. Well .. long story short.
Bashing as to the system beating up on me, or me beating up on the system ---- om -> which has the upper hand ?

Like they say ->
[INDENT][INDENT][INDENT]sometimes you bite the bear
[INDENT][INDENT][INDENT][INDENT]sometimes the bear bites you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

