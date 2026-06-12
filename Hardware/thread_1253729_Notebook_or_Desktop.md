---
title: "Notebook or Desktop"
date: 2009-08-30
forum: Hardware
---

### Post by Zilioum on 2009-08-30
I'm currently using a VAIO VGN-CR11Z Notebook. I quite like it but its getting a bit old and its doesn't really have enough power to run a Windows VM without laging too much. In a few weeks I'll start studying computer science at university so I figured this would be a good excuse to buy a new pc :P  
The problem is that I cant decide whether I should buy a powerful but expensive and heavy notebook or build myself a kickass desktop and use a rather weak but light and cheap notebook for university (I really like the DELL XPS M1330). 
Any experience with either of these scenarios? Is a weak notebook enough for university during the courses? How about syncing notebook and desktop? 

Cheers

---

### Post by IQRules on 2009-08-30
I have 1 HP NC6320, duo core, 15" LCD, 2GB, 120GB.
Got an offer for $275. Run Ubuntu 8.10 fine, but it has 32-bit CPU.

Well you are too far away.
It is kind of heavy though.

---

### Post by Zilioum on 2009-08-30
Thanks, but I would rather want to know what you would choose on a conceptual level. And if you had any experience with one or the other system.

---

### Post by SuperSonic4 on 2009-08-30
I was going to use my laptop for uni but found out it was still much easier to use a pen and paper for making notes

Therefore I would suggest building a desktop to use. Uni are probably obliged to provide computers that do the job anyway if you need one on-site

---

### Post by Zilioum on 2009-08-30
I don't think that I'll use pen and paper often, but I agree that if you need a powerful machine on the spot the will provide one or let you do it at home.

---

### Post by yossell on 2009-08-30
I have a Dell XPS1330 and I like it but there's a known issue with the versions that contain the nvidia8400 cards. A flaw in these cards together with Dell's poor heatsink arrangement has caused great problems. See, for instance, [http://forum.notebookreview.com/showthread.php?t=204772](http://forum.notebookreview.com/showthread.php?t=204772) and all the fuss there. Consensus seems to be: you're lucky if it lasts a year before terrible graphics problems arrive, though some people have been luckier.

It's possible and simple and cheap to mod the heatsink, replacing the terrible thermal pad Dell uses with a copper shim, which improves temperatures greatly and seems to mitigate the problem, but it's not ideal. The version of the M1330 that comes with integrated graphics is meant to be immune from this. If I were buying now, I would consider this, but if you're a gamer it may not be for you.

It's a shame, because apart from this flaw, I've found the M1330 to be a very good machine. I don't think the newer StudioXPS line faces quite the same problems, as the newer nvidia card is not meant to suffer from the same defect. However, there are some reports that they run quite hot. 

In general, I would always go with two systems - a light laptop for note taking, web browsing, useful university tasks, and a more powerful desktop which will run cooler and can be upgraded when necessary for extra power.

---

### Post by Zilioum on 2009-08-30
Thanks for your nice answer. I think I'll go with the two systems solution, really makes a lot more sense. Do you know if the heatsink problem persists with the 8600v cards? thats the one I would get from Dell here in Switzerland. How long does your battery last, really?:) And does Linux run well on it? Driver support etc.
As I understood from the info on the Dell homepage, the Studio is basically a more powerful version of the xps. 
I wouldn't use the laptop for gaming, that's what the desktop would for. But how much power (processor, ram, graphics card) to let me run a VM, have Compiz on "max" and in general a fast computer for everything except gaming (is onboard graphics enough ten?)

---

### Post by yossell on 2009-08-31
Hi Zilioum,

Unfortunately, those chips seem to be affected as well. See, for instance,
[http://www.engadget.com/2008/07/10/all-nvidia-8400m-8600m-chips-faulty/](http://www.engadget.com/2008/07/10/all-nvidia-8400m-8600m-chips-faulty/) 
Even if they didn't suffer this problem, I would still recommend the copper shim mod as the thermal pad construction is simply awful. It's all a bit annoying as, from what I can gather, nvidia cards have a reputation for working well with Linux. I don't know about Intel integrated graphics. 

Although my desktop is Linux ,my laptop, which is my primary working computer, is still windows, so I can't answer your questions. I have experimented with a live cd of Ubuntu 9.04 on the m1330 and *everything* relevant to me worked well - wireless card, touchpad, dedicated media buttons. I'm very close to moving over, but haven't quite worked up the nerve yet. One thing that worries me is that Ubuntu seems to be working the graphics card harder than vista  - indeed, before I did the copper mod, when experimenting with a live cd, the fans would come on at full speed after just a little use, and a couple of times, shut down for safety. 

In windows vista, bells and whistles off, the nine-cell battery currently lasts a little over five hours of continuous word-processing, on the power-saver plan. You'd probably get more if you went the integrated graphics route. 

The notebook forums I linked to earlier has a section on linux computers on notebooks:
[http://forum.notebookreview.com/forumdisplay.php?f=1029](http://forum.notebookreview.com/forumdisplay.php?f=1029)
It may be worth checking out some of those posts or asking about people's experience with linux on a laptop.

---

### Post by binbash on 2009-08-31
I am using Notebooks for 10-12 years. Desktops make more noise plus you can not carry them to everywhere. I would go for Sony Vaio or Mac. Do not buy anything then Vaios.

---

### Post by stefangr1 on 2009-08-31
> **binbash said:**
> I am using Notebooks for 10-12 years. Desktops make more noise plus you can not carry them to everywhere. I would go for Sony Vaio or Mac. Do not buy anything then Vaios.

Desktops do not make more noise by definition. I have used one notebook as my only pc for some years as well, but at home I was almost always working from the same spot. A few years ago I bought a desktop with nice 24" display (they're really cheap now, so I'd recommend getting one if you buy a desktop), and I must say I like it a lot more than my notebook. 

Working on it is just much more comfortable, especially when working on it the entire day.

---

### Post by Zilioum on 2009-08-31
What I'll do know is that I'll build a desktop and buy a light notebook as soon as I have enough cash again :P 
I'll think I'll go for a Dell notebook, just makes the best impression on me (apart from the overheating, but I might buy a "studio" anyway).

> I would go for Sony Vaio or Mac. Do not buy anything then Vaios. 

The last two pcs I had were both vaios. I think there ok, but value for money is a lot better with Dell. With Vaio you pay to much for the design. 

> One thing that worries me is that Ubuntu seems to be working the graphics card harder than vista

I use my old vaio desktop as a linux server and I also had problems with a loud graphics card. It was a very old ati card, and there is no software on linux to slow it down. I replaced it with a cheap fan-less one (as silent as it gets :)) you might have more luck with finding software to slow down your nvidia card, considering that its new and nvidia is generally better supported. But apart from that I think ubuntu on a notebook is great, it really shows you how slow Vista is in comparison.

I agree that a desktop is nicer to work on, especially with a 24" screen :)

---

### Post by yossell on 2009-08-31
> **Zilioum said:**
> But apart from that I think ubuntu on a notebook is great, it really shows you how slow Vista is in comparison.

Yes, I can well believe it. My involvement with Ubuntu was originally prompted by frustration at how sluggish my laptop felt under vista. I'm quite close to putting it on my m1330...just need to find a little more familiarity and courage...

---

### Post by Zilioum on 2009-08-31
> **yossell said:**
> Yes, I can well believe it. My involvement with Ubuntu was originally prompted by frustration at how sluggish my laptop felt under vista. I'm quite close to putting it on my m1330...just need to find a little more familiarity and courage...
Yes, I know what you mean, it also took me a long time to switch to ubuntu altogether and really do my everyday work on it. I had a dualboot system for a while (really easy to set up if Vista is installed first). Now I run a VM for the stuff I need windows for (Syncing my iPhone mainly).

---

