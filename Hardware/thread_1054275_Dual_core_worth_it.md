---
title: "Dual core worth it?"
date: 2009-01-29
forum: Hardware
---

### Post by theophile on 2009-01-29
I have a Dell Inspiron 1501 with an AMD Turion 64 2.0 ghz processor (MK-36). I'm considering upgrading it to a Turion 64 X2 2.0 (TL-60). To what extent is Ubuntu configured to make use of both cores? Would it be worth the effort?

---

### Post by GepettoBR on 2009-01-29
> **theophile said:**
> I have a Dell Inspiron 1501 with an AMD Turion 64 2.0 ghz processor (MK-36). I'm considering upgrading it to a Turion 64 X2 2.0 (TL-60). To what extent is Ubuntu configured to make use of both cores? Would it be worth the effort?

I'm afraid I won't be of much help, mate, but here's what I've got:

I'm on a dual-core system myself, and conky tells me that the load is evenly distributed between cores most of the time. If I have lots of applications open, Ubuntu sorts them out between the cores in what seems to me a very efficient way.

HOWEVER, the greatest benefit of multiple cores is not running several apps at once, but running threads from a same processor-intensive task in parallel (for example, video encoding, 3D modelling, password cracking and world domination). When that's the case, it's up to the application to manage the cores. A program that wasn't designed with specific support for multiple cores will send all of its requests to the same core while the other is simply ignored.

So, if you're a person who uses lots of programs at the same time like me, yes you'll have a certain benefit, especially in stability since you'll reduce the chances of overloading your CPU. But if you perform lots of CPU-intensive tasks, then it's up to each application supporting multiple cores, not the OS.

---

### Post by cubeist on 2009-01-29
In general, I would say moving to a dual-core chip is a good upgrade, but it depends on how much you are paying for the tl-60.  I have used a couple laptops with amd tl series chips and overall they work fine for most day-to-day applications (email, web, photo management, etc.) but will not wow you if you are doing anything intensive.

---

### Post by HittingSmoke on 2009-01-29
> **theophile said:**
> I have a Dell Inspiron 1501 with an AMD Turion 64 2.0 ghz processor (MK-36). I'm considering upgrading it to a Turion 64 X2 2.0 (TL-60). To what extent is Ubuntu configured to make use of both cores? Would it be worth the effort?

It really depends on how much multi tasking you do, and how CPU-intensive it is. For most desktop work you wont really **need** the extra core, but any time you're running several programs at once it helps.

---

### Post by uberdonkey5 on 2009-01-29
I use dell 1520 with dual core at home. As soon as I changed I noticed the difference of true multitasking. Basically you want a good memory (2GB RAM at least). My work computer is single core, and quite high specs, but I really notice that dual core does the multi-tasking well (and also with video editing, as previously mentioned). I am not one of these people that keeps loads of packages open, but almost always there are 2-3 programs running at one time. Ubuntu (and the modern packages) seem to manage the two cores very well.

Personally, I think the future is at least dual core. I would say DEFINITELY go for dual core, though I cannot comment on the specifics of the computer you are looking at.

---

### Post by Squid Spectre on 2009-01-29
GepettoBR is right about current day usefulness, but I would say dual-core processors are a worthwhile thing to invest in. You'll get longer and more pleasant life out of your machine. But that depends on what you want to use it for or how much you are stretched for cash.

---

### Post by electrogeist on 2009-01-29
When shopping for a new machine I'd say hell yes... but the OP has a similar single-core laptop now.  So it depends on how you use it and whether you have the $ to burn.  You can keep an eye on your cpu usage graph for a while too.

I've been a fan of having 2 CPUs since the Pentium 2 days

---

### Post by stchman on 2009-01-29
> **theophile said:**
> I have a Dell Inspiron 1501 with an AMD Turion 64 2.0 ghz processor (MK-36). I'm considering upgrading it to a Turion 64 X2 2.0 (TL-60). To what extent is Ubuntu configured to make use of both cores? Would it be worth the effort?

I would say no.  I would wait until your are going to get a new laptop and then get one with a dual or quad core.

Unless a drop in dual core is like $20 for that laptop.

---

### Post by theophile on 2009-01-30
The TL-60 is about $70 second-hand. Part of my motivation is a geeky desire to "pimp out" this cheapo budget laptop. I've already maxed out the RAM, installed a DVD burner and a 250GB hard drive. I've got a firewire card and I'm looking into one of those miniature USB bluetooth receivers. My next thoughts are the CPU and perhaps replacing the panel with a WUXGA panel.

I use this machine as a "mobile desktop." I do a lot of video editing and compressing also.

---

### Post by electrogeist on 2009-01-30
Ah, I thought you were looking to replace the laptop outright... and your OP even said "upgrade it" LOL

---

### Post by Neural oD on 2009-01-30
it's good to go for - especially if u doing intensive things - like ripping dvd's - yes u can rip your own dvd's legally - well where i live anyway. 
It can dramatically reduce the amount of time taken to rip! 
Obviously one needs software that is optimized for dual core - for one to really feel the benefits

---

### Post by cubeist on 2009-01-30
yes, for 70, that's not a bad upgrade.  I  think that chip retails for about 150 new.  One point of caution, have you actually taken your laptop apart to ensure that you have a removable cpu?  Some laptops have the cpu/northbridge soldered to the board...

---

### Post by GepettoBR on 2009-01-30
> **theophile said:**
> I do a lot of video editing and compressing also.

The compressing I get, but how in Hell can you get any decent editing done in Ubuntu? Linux NLEs are awful.

However, if you do a lot of editing and encoding, I'd say the Dual Core is more than worth it. This is exactly the kind of intensive operation in which multi-core processors shine the brightest.

---

