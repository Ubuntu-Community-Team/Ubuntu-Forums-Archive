---
title: "Acer Aspire 5720"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by xRes on 2008-01-05
Hello,
I have seen the article relating to my laptop 
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720")
But am not 100% sure how to do what it asks when talking about setting up the sound and compiz so could someone please help me and explain.
for example i dont understand how to get compiz to work. the guide talks about invoking it with script in the gnome session manager but i dont know how:

> To get Compiz-fusion working, you need to invoke it like this:

SKIP_CHECKS=yes compiz --replace

You can create a little script and put invoke it with the gnome session manager. 


appologies for my noobishness

Thanks is advance,
xRes

---

### Post by mezulig on 2008-02-05
try this:

$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

hugs
mezulig

---

