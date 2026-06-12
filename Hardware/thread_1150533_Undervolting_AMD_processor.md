---
title: "Undervolting AMD processor"
date: 2009-05-06
forum: Hardware
---

### Post by Bloemetjesgordijn on 2009-05-06
Hi,

I would like to undervolt my current AMD processor (Phenom 9550) Have to do it with an application, as my Motherboard does not support it [-(

I have found a linux tool PHC [http://www.linux-phc.org/]("http://www.linux-phc.org/")

According to their website there is an AMD patch floating around, but I havent found it.

Does anyone have any experience with this tool and AMD??

Cheerz

Bloemetjesgordijn

---

### Post by 444 on 2009-05-06
There is the k8fq utility. It is the fastest way to set one speed/voltage. Unfortunately it's not automatic.

I've used this on my Athlon64 before. No idea if it works on Phenoms (heard AMD redid PowerNow, breaking all the old undervolting techniques).

There indeed is indeed a PHC patch floating around too (someone posted it on a mailing list). I never got it working. Add to that the fact that it's probably based on an old kernel and never updated, plus how it's also broken by AMDs redone Powernow...


I suggest trying k8fq, if it doesn't work then the PHC patch won't work either. Let me know, I have a newer AMD (not the Athlon) cpu I can try things on if it doesn't.

---

### Post by nexus_2006 on 2009-05-06
Why do you want to undervo[t the CPU?

---

### Post by Bloemetjesgordijn on 2009-05-09
> **444 said:**
> There is the k8fq utility. 

Thx I will give it a try.....well   I found the website. The latest version is from April 2007 and according to the site might be working on a Opteron. I am a bit reluctant to install it...as:
1 might break m CPU
2 probably wont work
3 will break my allready working powernowd

> **nexus_2006 said:**
> Why do you want to undervo[t the CPU?


The CPU in my HTPC is making to much heat and doing nothing most of the time

---

