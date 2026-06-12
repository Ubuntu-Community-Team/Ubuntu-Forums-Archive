---
title: "How the multiprocessor work together"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Chafnan on 2007-04-24
I have a Intel Core 2 Duo.  When I am running processes on my computer the processors are running interesting.  One CPU will run to 100% and then they will switch so that the the other processor is running 100%.  Is there a fix in Ubuntu to get them to work together?

I have had a dual G5 Mac in the past and I remember the same thing happening with Panther, but when Tiger came out the processors always worked together.

Any help would be great.  Thanks

---

### Post by kidders on 2007-04-26
Hi there,

What you're describing is what is supposed to happen ... the OS is load balancing, to make sure one CPU doesn't get overworked. The reason only one CPU is being used at any one time is probably because the application you're running isn't multithreaded.

---

### Post by Chafnan on 2007-04-26
Why I am wondering is that when my Mac had Tiger installed on it the speed increased hugely with it.  As far as I could tell the only difference was the CPU's working together.

Is there any more resources out there that I could read more about this?

---

### Post by psusi on 2007-04-26
They never truly "work together".  Each cpu is capable of doing a separate task at the same time.  If you have two tasks, then each cpu can work on them independently, but a single task can only be assigned to one or the other at any given time.  Generally linux tries to keep a task on the same cpu it has been running on because that cpu already likely has a lot of the data that task uses cached, so it will be faster than switching it to the other cpu.  With one task running, that tends to have one cpu kept very busy while the other is idle.  Windows on the other hand, likes to keep swapping the task back and forth between cpus so that each one is 50% utilized.

---

### Post by kidders on 2007-04-26
**Edit:** Oops... I'm too slow!
[COLOR=Silver]
Hey again,

> **Chafnan said:**
> When I am running processes on my computer the processors are running interesting.You may already know this, but just in case, a single thread can't normally run on more than one processor. So, whether this is normal depends on whether you really mean "process**es**".

Multi-core processors don't always work the way you might think they do. For instance, running a single-threaded application on a dual core PC will never use 100% of both CPUs. Appearing to do so is quite often the result of *inefficiency* (ie the OS is eating up the other CPU, trying to keep up with the process running on the other one). Secondly, your CPUs are presumably sharing certain resources (eg memory interfaces) that will make it impossible to get full use of both CPUs at the same time, no matter how many threads are running.[/COLOR]

---

### Post by Chafnan on 2007-04-26
I have one more question then.  How is the Mac OS X setup to run dual core compared to linux?

EDIT:  One more question also.  Is a dual core processor run differant then a machine that has two physical processors?

---

### Post by kidders on 2007-04-27
Psusi may want to correct or add to this (please do!), but...

Not all applications support multithreading, and those that do tend to allow the feature to be switched off ... which is common, because it can cause stability problems.

Anyhow, there are a few different things going on here. Here are two examples:

**_Performance Optimisation_**
OSX has to deal with a _very_ small hardware library, and Apple strongly encourages developers to use its own software development platform, along with its custom development libraries (eg CoreAudio, etc.). This allows OSX to make some impressive optimisations, that might not be safe in other environments... such as multithreaded OpenGL.

Essentially, all the efforts of a massive multinational corproration are being focused on a single, very well-defined product (in contrast to MS & Linux). Given the prevalence of multi-core processors in the Mac world, you would expect that they've gotten certain things right hehe.

**_Smoke & Mirrors_**
OSX is tweaked to prioritise the UI ahead of most other tasks, so the interface feels fluid & responsive, even when the system is under high load. As a result, CPUs will be worked harder than they perhaps should be (ie harder than they are in Linux).

A simpler example of this sort of thing is where Microsoft converts, on hearing about Linux's (supposedly) superior memory management model, decide to check it out for themselves. Many are astounded by the sheer volume of memory Linux appears to use in normal operation, compared to something like XP. Without getting side-tracked, what they are in fact looking at is evidence of greater efficiency, not *in*efficiency.

So, to the end user, a heavily loaded OSX will "feel" more responsive; to the user armed with **top**, it will appear to be working more efficiently; but in reality, it could very easily be spending less time doing what it's *supposed* to be working on.



Both of these issues will impact performance on OSX, imo.


The other thing developers have to factor in is the overhead involved in working with multiple CPUs at the same time, which is considerable. Sometimes, it might be worth it (eg Blender) ... other times it just isn't (eg MSOffice). This is particularly relevant to your second question about multi-core processors versus multiple processors, which do tend to work quite differently.

Anyhow, back to Ubuntu. One of the things you will find about Ubuntu is that it's design is quite generic. It's optimised in such a way as to perform well on lots and lots of systems. Although you *can* optimise Linux to your own specific hardware (with a little effort), I would fully expect Psusi to agree that (at least in respect of multi-core CPU performance) you mightn't get very much out of it.

Part of my reason for saying that is this (and excuse the childishness of the example):

Imagine you had an adding machine composed of two independent microchips, that collected numbers from a third (shared) chip, and added them to a running total. Even though you effectively have *two* adding machines, they can only work as fast as the third chip can churn out numbers, and have to take turns when they want to fetch a new one. Furthermore, any time you wanted to know what the running total *was*, you wouldn't be able to answer the question without doing even more work.

I'm sure you can imagine that a professional software developer would be well able to argue that, in most cases, not bothering with the second adding machine is as fast, or *nearly* as fast, and *waaaay* more stable ... and in more realistic language too!
:lolflag:

Sorry for rambling on for so long... I hope some of that is useful.

---

### Post by Chafnan on 2007-04-27
That is great.  Thanks a lot to answering my question on that.  That makes sense.

Do you have any good thinks to places that I can learn how to optimize my system?

------------

My system:

Asus Z84JP Laptop
T7400 Intel Core 2 Duo
2GB 667Mhz Ram
Nvidia GeForce Go 7600 - 512 RAM

---

### Post by kidders on 2007-04-27
Well, there are two issues there. The first is the OS itself. In principle at least, an operating system that is too generic cripples your PC right from the start, by failing to make things like architecture-specific CPU operations available to the applications that sit on top of them. The other is the applications themselves, which won't necessarily do things in the most efficient way possible, even if the OS would let them.

Anyhow, Ubuntu's kernel (the core of the OS) is pretty good, although there's till plenty of room for general performance optimisations, if you feel so inclined, depending on what hardware you've got (or perhaps *haven't* got). In terms of applications, the trouble with Ubuntu & other similar distros that use pre-packaged binaries is that you never quite know what you're getting. As you might imagine, things are often built quite conservatively, so they will run properly on as many PCs as possible.

If you're interested in altering the way software interacts with your CPU(s), what you're basically talking about is compiling your OS (and everything you run on it) from source. By compiling out features you don't need, perhaps being a little risqué with code optimisations, and turning on advanced things (like multithreading) where available, you can fine-tune your Linux so it runs as fast as humanly (computerly?!) possible. I do this sort of thing from time to time ... in fact I'm in the process of it right now on a new box I bought, just to see how a generic Ubuntu install compares. By the time I'm done, I'll have been at it for about a week though!

So, that's the sort of thing you'd be looking for ... the Linuxy bits of the web are full of pages written by people who've tried various techniques for squeezing more out of their systems.

One observation worth making is that, on a Laptop, things will pretty much always perform less impressively than a full-size box ... mostly due to power & heat management. Regardless of whether what you're tweaking is something high-level (like CPU governors) or low-level (like a kernel recompilation), you need to be **_very_** careful not to kill your battery, overheat your CPU, or damage other hardware. Laptops aren't usually designed to be pushed too hard!

---

