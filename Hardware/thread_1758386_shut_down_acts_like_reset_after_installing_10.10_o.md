---
title: "shut down acts like reset after installing 10.10 on an HP p6774y"
date: 2011-05-14
forum: Hardware
---

### Post by ajlinzey on 2011-05-14
I installed Ubuntu 10.10 on an HP p6774y with an AMD Phenom II processor and if I try to shut down it does a restart instead of shuting down.

---

### Post by PhantmKllr on 2011-05-14
Does "reset" mean that it suddenly shuts off (instead of going through a shut down cycle)? I'm not sure what the problem is, but try booting from the CD, then shutting down. See if you're having the same problem.

My computer shuts down pretty fast (usually within 2-5 seconds), so maybe this behavior is normal for your computer.

---

### Post by ajlinzey on 2011-05-15
I meant restart, It logs me out, shuts down ubuntu and goes back to initial BIOS screen and loads Windows without powering down.
-Andy

---

### Post by PhantmKllr on 2011-05-15
Come to think of it, I do have a newer HP desktop (/w/ two monitors and a Phenom II, purchased from Costco), that sometimes does the same thing under Windows.

Maybe it's the computer? I'm going to check the HP support site for any BIOS updates. You should do the same.

---

### Post by ajlinzey on 2011-05-16
When I shutdown from windows it shuts down no restart unless I tell it to.
-Andy

---

### Post by PhantmKllr on 2011-05-17
Try installing the chipset driver for Linux from AMD (if any).

---

### Post by ajlinzey on 2011-05-19
I checked the amd web site and under download drivers I picked motherboard/chipset. Windows says the graphics card is a Radeon HD 4200, So for product line I picked  Radeon Integrated 4200 series and operating system linux x86 and it says a a new driver was released 5/9/2011. So I think this is the right driver but nowhere in the driver sekleting did I tell the website I had an AMD Phenom II cpu. It looks like the driver is a graphics diver not a a chipset driver which I was expecting. Is this the rigth driver?
-Andy

---

### Post by ajlinzey on 2011-05-24
I installed the new driver from AMD and if a try to shut down it restarts.
-Andy

---

### Post by PhantmKllr on 2011-05-24
I was able to find the product info page for your computer on the HP website. However, I wasn't able to find any drivers for your chipset on the AMD site.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02629593&lc=en&dlc=en&cc=us&os=4063&product=5049534&sw_lang=#N160]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02629593&lc=en&dlc=en&cc=us&os=4063&product=5049534&sw_lang=#N160")

---

