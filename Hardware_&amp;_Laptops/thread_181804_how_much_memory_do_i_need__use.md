---
title: "how much memory do i need / use?"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by shutupimpoor on 2006-05-24
I currently have 1gb of PC3200 RAM (2 x 512). How do I tell how much of that RAM I am using? I am considering upgrading, but I am not sure if I will notice any difference. I primarily use the computer for multimedia: music (Banshee) and videos (Totem). as well as instant messenging (gAim) and office suite. Sometimes I feel it is a little sluggish, how can I check how much memory I am using? I know I can hold 4GB.

---

### Post by Dr. Nick on 2006-05-24
[quote=shutupimpoor]I currently have 1gb of PC3200 RAM (2 x 512). How do I tell how much of that RAM I am using? I am considering upgrading, but I am not sure if I will notice any difference. I primarily use the computer for multimedia: music (Banshee) and videos (Totem). as well as instant messenging (gAim) and office suite. Sometimes I feel it is a little sluggish, how can I check how much memory I am using? I know I can hold 4GB.[/quote] 
Open a console and type **top **that will give your memory usage
Here is mine

```

[COLOR=Black]Mem[/COLOR]:   1036096k total,   599824k used,   436272k free,    39020k buffers
Swap:        0k total,        0k used,        0k free,   255684k cached

``` 

Linux is different from windows in how it uses memory, here is a explination of mine

Total physical memory is 1036096k of that 599824k is use. of the 599824k being used 255684 is cached which means it is not being used now by a running application, but has stuff cached in it that i might need shortly in the future.  To find your current mem usage of the apps running just subtract cache from the used.

Linux caches alot of stuff so the memory is not wasted. It tries to use as much ram as possible to save stuff you many need. This sounds bad but is actually quite good. Whats the pont of 1gig ram when you only use 300mb for running apps then go access the hd to get more, why not just load some hd stuff you may need into a cache so when you want it its right their

An upgrade probably isnt necesary, but if you do you may need a different kernel to take advantage of it

---

### Post by khightower on 2006-05-24
System>Administration> System Monitor

Once you have system monitor running click on the "Resources" tab.

The 2nd row of data show Memory and Swap File usage

---

### Post by user1397 on 2006-05-24
[quote=khightower]System>Administration> System Monitor[/quote] its actually System->System Tools->System Monitor (i know, so many systems...:))
You can also check your memory usage (in kilobytes):
```
free
```
or in megabytes:
```
free -m
```

---

### Post by shutupimpoor on 2006-05-24
Thanks

---

