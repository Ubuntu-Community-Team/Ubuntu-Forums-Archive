---
title: "does swap space considerably increase performance"
date: 2008-08-02
forum: General Help
---

### Post by je1117 on 2008-08-02
I am about to install Ubuntu on my laptop, and it has 128mb of RAM on it. I have only used Ubuntu on my desktop which has 2gb of RAM, so I never really could tell if there was a performace increase due to my swap space. Getting a new HD for the laptop with 80gb of space - will making a large swap space, like 2 gb, show me a considerable performance increase? Or should I just stick with the rule of thumb, being double the RAM you have for the swap space. Thanks.

---

### Post by kostkon on 2008-08-02
> **je1117 said:**
> I am about to install Ubuntu on my laptop, and it has 128mb of RAM on it. I have only used Ubuntu on my desktop which has 2gb of RAM, so I never really could tell if there was a performace increase due to my swap space. Getting a new HD for the laptop with 80gb of space - will making a large swap space, like 2 gb, show me a considerable performance increase? Or should I just stick with the rule of thumb, being double the RAM you have for the swap space. Thanks.
With only 128MB of RAM you'll sure need swap, you cannot do otherwise. I don't think the system would boot without swap.

Anyway, with such a low RAM amount you will not able to use the *LiveCD*. The *LiveCD* needs at *least 256MB RAM*. You'll have to use the *Alternative Install CD*.

More of the *Ubuntu* requirement [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

You can just let *Ubuntu* decide how much swap space is needed (i.e. the size of the swap partition).

But, I believe [*Xubuntu*]("http://www.xubuntu.com/") would be more appropriate for this system.

---

### Post by jualin on 2008-08-02
I have heard that too much Swap will decrease performance, but I have never tried it myself.

---

### Post by fragos on 2008-08-02
Swap space doesn't improve performance it allows you to run more simultaneous applications than you have memory for. To improve performance, add memory until swap space is rarely used. In my case that was at the 1GB level although 512 performed well. With 128 you may not have enough memory to run Ubuntu, try Xubuntu which uses a much slimmer desktop manager than Gnome. The "free" command will tell you what your memory use looks like.

---

### Post by jualin on 2008-08-02
> **fragos said:**
> The "free" command will tell you what your memory use looks like.

Nice command, thanks!

---

### Post by PurposeOfReason on 2008-08-02
You'll need swap, despite what anyone tells you. I have 4GB of RAM and I have swap. You can't hibernate without x amount of swap I, I forget the exact number so it is important for laptops.

---

### Post by je1117 on 2008-08-02
I just checked and I have 256mb of RAM. And I've been married to the alternate CDs for a couple of years now so that's not an issue.

If assigning more swap space means running more programs simultaneously, doesn't that mean it would increase performance?

I would imagine it would only to an extent, or else no one would ever buy RAM. They would just make a big swap space. Just want to know the best for my setup. It's a Pentium III - 750mhz.

---

### Post by fragos on 2008-08-02
The kernel tries to keep a balance between available cache space and swap memory.  There is a "swappiness" parameter that it uses to weight that decision.  It's value can range between 0 and 100 with the default being 60.  100 keeps cache memory free by swapping often even if everything will fit in memory.  0 causes applications to shrink cache size to avoid swapping.  If you're running on a laptop and want to give your drives a chance to spin down and save battery power, use 20 or less.  The information I've found is more trend than scientific but it does give you basis of understanding and the ability to experiment a bit.  Believing that 100% is never an answer I chose a value of 10 and with 1GB of memory, I rarely find anything in swap space.  IMHO the elimination of swap space may be risky.

You can change swappiness by doing the following:

sudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.  In my case "vm.swappiness=10".

---

### Post by Diabolis on 2008-08-02
> **kostkon said:**
> I don't think the system would boot without swap.

Yes it will, I worked without swap for a while.

---

### Post by kostkon on 2008-08-02
> **Diabolis said:**
> Yes it will, I worked without swap for a while.
I meant that I don't think that with only 128MB RAM and no swap the system would cope.

---

### Post by CatKiller on 2008-08-02
> **je1117 said:**
> If assigning more swap space means running more programs simultaneously, doesn't that mean it would increase performance?

It's a trade-off between poor performance and no performance at all.

> I would imagine it would only to an extent, or else no one would ever buy RAM. They would just make a big swap space.

RAM access times are in the nanoseconds. Hard drive access times are in the milliseconds. If you're having to read from swap all the time ("[thrashing]("http://en.wikipedia.org/wiki/Thrash_(computer_science)")") performance is very much degraded, since the time spent shuffling data around between RAM and disk completely dwarfs the time spent actually getting anything done. More swap space isn't going to help this.

You'll need some swap space for some tasks. As PurposeOfReason says, you need the swap to hibernate - the data from RAM has to go *somewhere*, since the RAM is going to be turned off.

In your case, the only two realistic options are to either put more RAM in or to use a lighter environment.

---

### Post by jerome1232 on 2008-08-03
Yeah all swap does is instead of the computer crashing when it runs out of ram, it'll start using swap, if you run out of swap and ram your computer will crash.

So as the poster above me said more swap won't mean more performance, just no crash..

---

