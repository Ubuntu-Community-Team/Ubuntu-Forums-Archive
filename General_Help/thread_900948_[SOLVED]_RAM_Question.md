---
title: "[SOLVED] RAM Question"
date: 2008-08-25
forum: General Help
---

### Post by fparedesg on 2008-08-25
I have 2 gigs of RAM. When I open up the Task Manager with Windows, it says I have 2,403 of RAM, however, when I open up the System Monitor in Ubuntu (Hardy), it says that I have 986 MB. Why? Thanks to anyone who helps!

---

### Post by xeth_delta on 2008-08-25
Please open a terminal, and type:
```
free -m
```
Please post the output.

---

### Post by fparedesg on 2008-08-25
```
federico@Anchova:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           985        849        136          0         16        300
-/+ buffers/cache:        532        453
Swap:          831          0        831
federico@Anchova:~$ 
```

---

### Post by xeth_delta on 2008-08-25
> **fparedesg said:**
> ```
federico@Anchova:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           985        849        136          0         16        300
-/+ buffers/cache:        532        453
Swap:          831          0        831
federico@Anchova:~$ 
```

The situation you are describing is most unusual... Indeed, the reported amount of memory is 985 MB.

Could you please offer us the specs of your machine? The amount of memory you have (or what is reported by windows) on it is slightly unusual (not a power of 2), but not impossible to have. How have you installed the total amount to get that number?

Are you perhaps also using an on-board graphics card?

---

### Post by davidsrsb on 2008-08-25
I see little point in having huge ram and then strangling the memory bandwidth by using shared video memory on board graphics

---

### Post by xeth_delta on 2008-08-25
> **davidsrsb said:**
> I see little point in having huge ram and then strangling the memory bandwidth by using shared video memory on board graphics

I am not sure I understand what you mean.

Not quite true for mobile systems, as in most cases on-board solutions are the ones being used. They are quite efficient, too, from an energy poit of view. Now, performance-wise is a completely different matter, but in most cases, it's enough for compiz and even some not so new 3D games.

By the other hand, it is not the memory that is being slowed down by using an on-board card, it's the other way around. Regular RAM is way slower than GRAM, and is a great contributor to the poor performance of most on-board cards.

Also, again for mobile computers, it can be quite normal to have a lot of RAM and a slow graphics card, it all depends on what you do with your computer. I for instance do some University work that requires a lot of RAM, and not so much performance from the graphics card.

---

### Post by fparedesg on 2008-08-26
You guys are fast...

I'm on a Lenovo Thinkpad with a Core Two Duo 2.2 Ghz, both video and audio are integrated. I don't think it's a problem with my graphics card, when I installed Ubuntu I followed the "guided" setup and the disc made my partitions and everything. Maybe it also decided I needed less RAM for some reason? It seems the computer is using only the 900 that are "installed". I really don't need this urgently but i would love to use my new laptop to its full potential :).

---

### Post by xeth_delta on 2008-08-26
> **fparedesg said:**
> You guys are fast...

I'm on a Lenovo Thinkpad with a Core Two Duo 2.2 Ghz, both video and audio are integrated. I don't think it's a problem with my graphics card, when I installed Ubuntu I followed the "guided" setup and the disc made my partitions and everything. Maybe it also decided I needed less RAM for some reason? It seems the computer is using only the 900 that are "installed". I really don't need this urgently but i would love to use my new laptop to its full potential :).

Hehe, I'm writing for a disertation and checking the forums, so I'm able to reply fast ;)
Back on-topic. The graphics card will abviously be taking some of the memory. My machine is not that much different from yours (a different brand, though) and the graphics card is assigned 64MB of RAM out of 1024MB.

Still, the number Windows is reporting to you seems funny to me, too, 2403MB. Have you installed additional RAM modules?

I wonder if for some reason a rather large amount of memory is meing assinged to your graphics card. Can you check that in the BIOS, whether you can lock a predefined amount?

Regarding the free -m report. Actually, your programs are using only 453MB, the rest being buffers and cache to make the system run faster.
To this end, Linux will always try to fill all RAM that is free this way. Whenever more memory is needed by regular programs, the chache/buffer one is released accordingly.

---

### Post by fparedesg on 2008-08-26
Epic fail. I was checking the Task Manager's memory, but not the actual RAM used. The actual RAM is the same as in Ubuntu...

---

### Post by davidsrsb on 2008-08-26
I would run the the memtest86 in the boot menu to test that all is well with your ram. What size does this discover?
Some PCs do not like mixing memory stick sizes or even brands.

Linux does not "decide" to use less ram than available, although the kernel is sometimes built unable to use more than certain sizes, but I believe that Ubuntu supports >4GB

---

### Post by xeth_delta on 2008-08-26
> **fparedesg said:**
> Epic fail. I was checking the Task Manager's memory, but not the actual RAM used. The actual RAM is the same as in Ubuntu...

hehe, things like these can happen :p
It would have been an... interesting problem to solve, though.

In conclusion, you have 1GB of ram on the comuter, right? Of which, a part is dedicated to the graphics card.

Anyway, if the problem is solved, please mark the thread as solved.

---

### Post by davidsrsb on 2008-08-26
Our posts crossed
So it is a 1GB machine with shared video memory

---

### Post by fparedesg on 2008-08-26
Just to be 100% sure, I'm going to open up my laptop and check to see how much RAM I have, but that will have to be done tomorrow. I have to go to sleep now. Thanks for all your help!

---

### Post by xeth_delta on 2008-08-26
> **fparedesg said:**
> Just to be 100% sure, I'm going to open up my laptop and check to see how much RAM I have, but that will have to be done tomorrow. I have to go to sleep now. Thanks for all your help!

No problem, but I believe the BIOS should have that information.

---

### Post by neur0 on 2008-08-26
Do
```
 sudo dmidecode -t17 |grep Size
```
And you don't need to open your laptop

---

### Post by fparedesg on 2008-08-26
> **neur0 said:**
> Do
```
 sudo dmidecode -t17 |grep Size
```
And you don't need to open your laptop

Thanks for the info! I did that and I got ```
federico@Anchova:~$ sudo dmidecode -t17 |grep Size
	Size: 1024 MB
	Size: No Module Installed
federico@Anchova:~$ 

```
Looks like I just have one installed.

---

### Post by xeth_delta on 2008-08-26
> **neur0 said:**
> Do
```
 sudo dmidecode -t17 |grep Size
```
And you don't need to open your laptop

That's one useful command I did not know. I guess one learns new things each day.

---

### Post by xeth_delta on 2008-08-26
> **fparedesg said:**
> Thanks for the info! I did that and I got ```
federico@Anchova:~$ sudo dmidecode -t17 |grep Size
	Size: 1024 MB
	Size: No Module Installed
federico@Anchova:~$ 

```
Looks like I just have one installed.

BTW, from that command it can be seen that your laptop has two banks, of which only one is used with a 1024MB module.

---

### Post by fparedesg on 2008-08-26
> **xeth_delta said:**
> BTW, from that command it can be seen that your laptop has two banks, of which only one is used with a 1024MB module.

Yup yup, I noticed that. Looks like I'm gonna have to fill that uup...

---

### Post by arepaking on 2009-01-06
Does anyone knows how to check how much RAM is being used by video?

---

