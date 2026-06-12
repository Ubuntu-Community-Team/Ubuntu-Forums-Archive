---
title: "intel 945gm"
date: 2010-09-18
forum: Hardware
---

### Post by koorosh01 on 2010-09-18
hi ..
i have recently installed ubuntu 10.4 on my laptop (Tecra A8 PTA83E). it seems that all of my hardwares works fine . but i think my graphic card has low performance than windows.
for example when i run google earth on windows it works fine but when i run google earth on ubuntu , it works slowly..

how can i get the same windows performance for my graphic card on my ubuntu system?
thansk for your help

---

### Post by IcarusR on 2010-09-18
I have the same graphics card in my Tosh Equium A100-306 & Google Earth 
5.2.1.1329 (beta) works well. Never tried it under windows.

What version of google Earth are you using ?

---

### Post by Lateralis on 2010-09-18
Have you installed the (closed source)proprietary drivers (System -> Administration -> Hardware drivers) or are you running on open source drivers?

---

### Post by IcarusR on 2010-09-18
There are no proprietary drivers available in 'Hardware drivers' so I'm using open source.

---

### Post by Lateralis on 2010-09-18
Oh, wait a minute.  I totally misread the title of the thread.  

Intel hardware is well supported with modules built directly into the kernel.  So I'm quite perplexed that you're encounting performance issues. 

Off the top of my head I can't think of any reasons why Google Earth would be running slow, except that maybe Google Earth just doesn't run well on Linux.  

So, do you notice any other times when the graphics performance seems low?  Do you have desktop effects switch on or make use of Compiz for additional desktop compositioning effects?  If yes, do they work OK without problems?  

If you only notice a problem with Google earth, then the fault could lie with the Google Earth linux software, rather than the Intel kernel module.

---

### Post by davidmohammed on 2010-09-18
have a look [here]("https://help.ubuntu.com/community/GoogleEarth") - there are some hints and tips how to speed up google earth performance.

---

### Post by koorosh01 on 2010-09-18
my google earth version is 5.1.3533.1731 .
my desktop effects is on and my compize works well , i dont have any problem with them.

do i need to edit some configuration file such as xorg.conf or something like that?

---

### Post by IcarusR on 2010-09-24
> google earth version is 5.1.3533.1731

I am using version 5.2.1.1329 (beta), suggest you download it from google earth site & try it.

---

