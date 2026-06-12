---
title: "Laptop Recommendation"
date: 2011-02-04
forum: Hardware
---

### Post by Lucrin on 2011-02-04
I am looking at buying a laptop which I plan to use as strictly a linux machine to work on code and programming. I am currently a computer science major in college so a mobile programming platform would be useful to me. So far I have been looking at getting the HP g62x series, so I was wondering if anyone here has used that laptop and knows how it works with Ubuntu, or if anyone see's a potential problem?

Secondly I wanted to just get others opinions on other potential laptops I can get. Like I said, I intend to just code and do basic web browsing on it so it doesn't need a ton of power. Trying to keep things less than $600. (Student budget lol) Thanks!
[]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Everyday+computing&series_name=G62x_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Everyday_computing/G62x_series")

---

### Post by Lucrin on 2011-02-04
Come on now I know you guys all have opinions you are just bursting to share with everyone lol.

---

### Post by cprofitt on 2011-02-05
I personally have stuck with Lenovo laptops. In particular the T-series.

---

### Post by duanedesign on 2011-02-05
I would get an NVIDIA graphics card over an ATI. The Linux drivers for NVIDIA seem to work better. 

I have an HP G-60 120us, cost me $500 and I love it.

Canonical has an [Ubuntu Certified Hardware]("http://www.ubuntu.com/certification/") program.

[Community reviewed hardware.]("https://wiki.ubuntu.com/HardwareSupport/") Also some links at the bottom of the page for more resources.

[Linux HCL is a user review forum]("http://linuxhcl.com/")

---

### Post by cascade9 on 2011-02-06
The G62x should work, but you might need to play with the wireless to get it going- 

[http://georgia.ubuntuforums.org/showthread.php?t=1645716](http://georgia.ubuntuforums.org/showthread.php?t=1645716)

> **duanedesign said:**
> I would get an NVIDIA graphics card over an ATI. The Linux drivers for NVIDIA seem to work better. 

I have an HP G-60 120us, cost me $500 and I love it.

Canonical has an [Ubuntu Certified Hardware]("http://www.ubuntu.com/certification/") program.

With all the optimus/hybrid grpahics iX/nvidia setups, nvidia is actually a bad choice now. Optimus has 0 support, and in most cases the best you can do is shut off the nvidia GPU in the BIOS. A lot of the optimus laptops dont even have that option, so the nvidia chip just eats power. 

The certified hardware list is a joke. There are laptops listed there that have several different sub-models, and canonical dont give a full list of the tested hardware. So you could easily get a xxxxx-yyyyy laptop with an nvidia card, thinking that because it was on the certified list it would be fine, but the model tested only had intel graphics.....so the nvidia GPU you paid more for is useless in linux, or worse still, just draining power. 

IMO Intel video should work well (as long as that dont do something horrible but AFAIK they havent done anything like the GMA500 again). 

ATI should work as well, but its best to avoid multipule GPUs ('switchable graphics'). You can get ATI switchable graphics going in at least some cases, but its not worth the effort, and you probably wont find anything in the student budget with switchable graphics. 

nVidia is fine, as long as you dont have hybrid graphics or optimus. Since most of the laptop manufacturers never list hybrid or optimus in the spec, its best to avoid nvidia unless you know for sure that its a standalone nvidia GPU with no intel graphics at all (difficult to figure out, and now rare with most of the current intel CPUs).  

BTW, is there any way to put in a request to canonical to get a full specs list on the certified hardware list? It might be worth having with full hardware listing, and should only take, what, 30 secodns to do....  

> **duanedesign said:**
> [Community reviewed hardware.]("https://wiki.ubuntu.com/HardwareSupport/") Also some links at the bottom of the page for more resources.

[Linux HCL is a user review forum]("http://linuxhcl.com/")

They might be more usefull, I havent had a good look yet. ;)

---

### Post by Lucrin on 2011-02-06
Thanks everyone, I will continue looking into these options :)

---

