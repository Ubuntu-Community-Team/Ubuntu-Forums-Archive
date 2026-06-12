---
title: "My ram is going to be FULL"
date: 2010-06-17
forum: Hardware
---

### Post by emanamini on 2010-06-17
First forgive me for bad English writing
Second I have a question
I use UBUNTU 10.04 and after 20 min my ram is going to be full and my system is going to freeze 
What can I do ?
Many thanks

---

### Post by flowheat on 2010-06-17
I'm interpreting your question as saying that you think your RAM is all being used up quickly and when it gets full that you expect your system to crash.  If that's not the case then disregard my answer.

What are you actually using to determine that your RAM is all used up?

Chances are it's just reporting that your RAM is all cached which is how a Linux system operated.  It leaves things cached in memory in case they are accessed again soon so that they can be opened quickly.

Here's a good article on how to actually determine how much RAM is "in use"

[http://mail.nl.linux.org/linux-mm/2003-03/msg00077.html]("http://mail.nl.linux.org/linux-mm/2003-03/msg00077.html")

---

### Post by steveneddy on 2010-06-17
Please post the output of 

```
free -m
```

---

### Post by emanamini on 2010-06-19
> **steveneddy said:**
> Please post the output of 

```
free -m
```
Thank u for answer
Iwas not on my desk for two days 
forgive me
this is the out put of free-m
```
total       used       free     shared    buffers     cached
Mem:           497        481         15          0         32        191
-/+ buffers/cache:        258        239
Swap:         1906          0       1906
```

---

### Post by uOpt on 2010-06-19
> **emanamini said:**
> First forgive me for bad English writing
Second I have a question
I use UBUNTU 10.04 and after 20 min my ram is going to be full and my system is going to freeze 
What can I do ?
Many thanks

The OS already uses almost all RAM.

How do you know you will "freeze"?

---

### Post by BlacqWolf on 2010-06-19
how about adding more swap space? since i have a large HD, I usually add like 30gb

---

### Post by iponeverything on 2010-06-19
The recommended amount or RAM for 10.04 is 1 Gig, you have 512 Megs. 

Xubuntu has lower RAM requirements. It should work much better for you.

---

### Post by sanderd17 on 2010-06-19
> **BlacqWolf said:**
> how about adding more swap space? since i have a large HD, I usually add like 30gb
The problem is that the HDD is much slower than RAM. If you put working parts of your OS in swap, your system will look like it's frozen but in fact it will be using all its power to move bytes from HDD to RAM and back.

Since the system only has 512 MB RAM, it will not run well on Ubuntu. Maybe a tip is to set the swap partition of. Your computer will stay active but it won't open a new program if the RAM is almost full. At least, it won't use swap in an inefficient way. To switch swap of, use
```

sudo swapoff -a

```

to switch back on:
```

sudo swapon -a

```

As said, you won't be able to open certain apps (If I were you, I won't even try Firefox or openoffice. Gedit and nautilus may work)

you'll better switch to a lighter derivate of Ubuntu. Xubuntu is well known (and thus good supported) but I've heard that it's becoming more heavy too. Another option is Lubuntu, it's quite new (so it has some extra bugs) but I've heard good things of it.

---

