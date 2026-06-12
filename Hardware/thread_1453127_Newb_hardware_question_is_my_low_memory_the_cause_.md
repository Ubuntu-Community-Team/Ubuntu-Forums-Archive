---
title: "Newb hardware question: is my low memory the cause of this?"
date: 2010-04-12
forum: Hardware
---

### Post by TheNerdAL on 2010-04-12
When I open programs, they tend to take not quite that fast to open. Should I add more ram? I have like around 512 mb or so of ram. I'm saving up money to upgrade my computer and going to buy 2 GB (Two 1 GB PCI's).

---

### Post by Slim Odds on 2010-04-12
Sound good to me....

---

### Post by cascade9 on 2010-04-13
Check htop for your RAM and CPU usage. 

If you are using most of your RAM, and/or have much in the way of swap usage, its caused by RAM shortages and adding more RAM will help. If not..then adding more RAM wont help at all. 

If you have low RAM usage but high CPU usage, your slowdowns are caused by lack of CPU.

---

### Post by TheNerdAL on 2010-04-13
> **cascade9 said:**
> Check htop for your RAM and CPU usage. 

If you are using most of your RAM, and/or have much in the way of swap usage, its caused by RAM shortages and adding more RAM will help. If not..then adding more RAM wont help at all. 

If you have low RAM usage but high CPU usage, your slowdowns are caused by lack of CPU.

[IMG]http://i43.tinypic.com/24c5r8k.png[/IMG]

Is that bad? O.o 

That is without Desktop effects enabled.

---

### Post by cascade9 on 2010-04-14
Serveral things I notice-

1- 253 of 370MB RAM used. Not that bad, considering that you are running a web browser..but I thought that you have 512MB? Something you need to check. 

2- 111MB Swap is being used- so more memory will help.

3- X (graphical interface) is using a lot of CPU. That will be slowing everything down. 

Not sure on the following- 

4- 238 tasks? o.O At the momnet I dont have a running *buntu box to check that against, but it seems awfully high (my current sidux  KDE4.3 install has more like 135 tasks).

---

### Post by Slim Odds on 2010-04-14
> **cascade9 said:**
> Serveral things I notice-

1- 253 of 370MB RAM used. Not that bad, considering that you are running a web browser..but I thought that you have 512MB? Something you need to check. 

2- 111MB Swap is being used- so more memory will help.

3- X (graphical interface) is using a lot of CPU. That will be slowing everything down. 

Not sure on the following- 

4- 238 tasks? o.O At the momnet I dont have a running *buntu box to check that against, but it seems awfully high (my current sidux  KDE4.3 install has more like 135 tasks).

I agree, it looks like it's 384MB of RAM and not 512. I have an older machine running 8.04 with 384MB and it works OK, but it is a little slow due to that small memory space.

238 tasking but only 1 running  :P

Definitely needs some more memory. It's very cheap these days and it makes the most difference in a case like this.

P.S. Now we have to see these **ugly** purple screen dumps and I do mean dumps

---

### Post by TheNerdAL on 2010-04-14
> **cascade9 said:**
> Serveral things I notice-

1- 253 of 370MB RAM used. Not that bad, considering that you are running a web browser..but I thought that you have 512MB? Something you need to check. 

2- 111MB Swap is being used- so more memory will help.

3- X (graphical interface) is using a lot of CPU. That will be slowing everything down. 

Not sure on the following- 

4- 238 tasks? o.O At the momnet I dont have a running *buntu box to check that against, but it seems awfully high (my current sidux  KDE4.3 install has more like 135 tasks).

I was just running a web browser. O.o And why does it say 370 MB total of ram when I think I have 512 MB?

---

### Post by Slim Odds on 2010-04-14
> **TheNerdAL said:**
> I was just running a web browser. O.o And why does it say 370 MB total of ram when I think I have 512 MB?

By far the easiest way to check is to open the box and see what's inside.

---

### Post by cascade9 on 2010-04-15
> **TheNerdAL said:**
> I was just running a web browser. O.o And why does it say 370 MB total of ram when I think I have 512 MB?

Could be that some memory is being shared to your onboard video. It shouldnt be using 142MB, but you never know. 

253MB + 111MB swap is pretty awful if yuo only have a browser running. 

BTw, how many instances (and/or tabs) did yuo have open with chrome when you took that screenshot? It looks like it is using a lot of memory. 

> **Slim Odds said:**
> By far the easiest way to check is to open the box and see what's inside.

+1. ;)

---

### Post by Yellow Pasque on 2010-04-15
> **Slim Odds said:**
> By far the easiest way to check is to open the box and see what's inside.

Being physically lazy, errr energy-efficient, I would try dmidecode first:
```
sudo dmidecode -t memory
```

---

