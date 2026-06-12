---
title: "How much SWAP partition is needed if RAM is 6 Gb??"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by leonardo_neo on 2009-01-07
Dear members,

I wish to install ubuntu in my new laptop. I wish to install 64bit OS, so I have installed 6 Gb RAM.

As a general rule, I had read somewhere that the swap partition should be double of RAM size, as if 'n' is RAM size so the swap partition should be 2n.

I want to know, do I have to create 12Gb of swap? I know this question is really stupid for most of you, but I believe most of the newbies like me don't know this.

If not 12 Gb, then how much should be the ideal size of swap partition, if RAM is 6 Gb?

I have searched for similar threads, but didn't find any answer, so kindly bear it.

Thanks in anticipation. :)

---

### Post by oldos2er on 2009-01-07
Unless you plan on using hibernation, a 512MB swap partition would be more than enough, IMO.

---

### Post by oilchangeguy on 2009-01-07
> **oldos2er said:**
> Unless you plan on using hibernation, a 512MB swap partition would be more than enough, IMO.

i agree.

---

### Post by halovivek on 2009-01-07
> **leonardo_neo said:**
> Dear members,

I wish to install ubuntu in my new laptop. I wish to install 64bit OS, so I have installed 6 Gb RAM.

As a general rule, I had read somewhere that the swap partition should be double of RAM size, as if 'n' is RAM size so the swap partition should be 2n.

I want to know, do I have to create 12Gb of swap? I know this question is really stupid for most of you, but I believe most of the newbies like me don't know this.

If not 12 Gb, then how much should be the ideal size of swap partition, if RAM is 6 Gb?

I have searched for similar threads, but didn't find any answer, so kindly bear it.

Thanks in anticipation. :)
Since you have 6GB of RAM you dont have to have swap. but if you  want just create 1GB for safer side. if you load of applications like that. but even it will not take that. 
my experince.:P

---

### Post by donfletcher on 2009-01-07
With 6GB of real ram, you may never need to use swap. but if you do need to use swap. it is unlikely that anything less than a gig would do you any good. Just think how likely it will be that you will need more than 6 gig but less than 7.

---

### Post by halovivek on 2009-01-07
> **donfletcher said:**
> With 6GB of real ram, you may never need to use swap. but if you do need to use swap. it is unlikely that anything less than a gig would do you any good. Just think how likely it will be that you will need more than 6 gig but less than 7.

Yes it will not do anything as you said. if you want, you can go ahead with just 256MB also.

---

### Post by DeMus on 2009-01-07
> **halovivek said:**
> Yes it will not do anything as you said. if you want, you can go ahead with just 256MB also.

I have 4GB of RAM and I use zero. At the moment I have 5 programs running and need just 650MB RAM.
When you have enough memory (>2GB) you probably won't ever use swap memory, unless you plan to do extraordinary things with your computer.

Just try it and keep track of the system monitor (tab resources) when PC is under heavy load. Just watch how much ram you are using.
Success.

DeMus

---

### Post by stream303 on 2009-01-07
The only consideration here would be if you ever intend to hibernate - then I'd just set swap at 6gb.  But under normal operating circumstances, you'll never touch it.

---

### Post by paris_alex on 2009-01-07
didn't know hibernate uses swap partition. so did a quick search on this and found out even more... 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Looks like we can also create a swap file instead of a swap partition! interesting...

---

### Post by Sasquatch2000 on 2009-01-07
Isn't that how VAX's and Windows does it? You don't need a separate partition for them, just a separate swap FILE.

---

### Post by leonardo_neo on 2009-01-08
> didn't know hibernate uses swap partition. so did a quick search on this and found out even more...

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Looks like we can also create a swap file instead of a swap partition! interesting...
__________________

Thank you all for showing your interest to answer my questions. The link posted by a member shown above also satisfied most of my queries. So the conclusion is

1. If you have big RAM, then probably you wont need swap memory.

2. If you plan to have hibernation function, then you need to have swap partition atleast the size of your RAM.

3. Even after installation OS, if one wishes, swap can be increased.

Now I know how much swap I will create while installing Ubuntu.

Thank you all. :)

---

### Post by halovivek on 2009-01-09
> **leonardo_neo said:**
> Thank you all for showing your interest to answer my questions. The link posted by a member shown above also satisfied most of my queries. So the conclusion is

1. If you have big RAM, then probably you wont need swap memory.

2. If you plan to have hibernation function, then you need to have swap partition atleast the size of your RAM.

3. Even after installation OS, if one wishes, swap can be increased.

Now I know how much swap I will create while installing Ubuntu.

Thank you all. :)

So you got the perfect answer. thats really great.

---

