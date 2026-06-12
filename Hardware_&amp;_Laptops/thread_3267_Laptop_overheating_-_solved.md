---
title: "Laptop overheating - solved"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by knappen on 2004-11-04
I installed Ubuntu on my laptop with a AMD Mobile processor. Everything ran perfectly except the laptop got really hot and the battery life did not really have a life at all :-)

ubuntu-geek sugested I submit a bug, and I did. Problem is now solved.

There was one module that I needed to get the CPU frequency scaling to work that was not loaded. So if there is anyone out there with a really hot laptop using the AMD Mobile processor this is the module you have to load

powernow-k7

Edit /etc/modules and add powernow-k7 on a seperate line and reboot.

That worked wonders for me!

We really need a seperate forum for laptops

---

### Post by Jspired on 2004-11-04
[QUOTE=knappen]

We really need a seperate forum for laptops[/QUOTE]

I would agree!  Glad to see you're up and running cooler!

---

### Post by HungSquirrel on 2004-11-04
[http://ubuntuforums.org/forumdisplay.php?f=19](http://ubuntuforums.org/forumdisplay.php?f=19)

---

### Post by knappen on 2004-11-04
[QUOTE=HungSquirrel][http://ubuntuforums.org/forumdisplay.php?f=19](http://ubuntuforums.org/forumdisplay.php?f=19)[/QUOTE]
 Ha ha, there you go!

It must just recently been added. Perfect!

Ubuntu is just getting better and better and this forum is growing by the day.

---

### Post by wulle on 2004-11-05
hoi,
after reading your topic I also loaded this module , it works very well !

thx
wulle

---

### Post by knappen on 2004-11-05
[QUOTE=wulle]hoi,
after reading your topic I also loaded this module , it works very well !

thx
wulle[/QUOTE]
 Good to hear!

I think it is always a good idea to post the solution to a problem. The chance that someone else has the same problem is probably high, especially since this is the first release. A very good first release I might add.

---

### Post by Johan on 2004-11-05
[QUOTE=knappen]
powernow-k7

Edit /etc/modules and add powernow-k7 on a seperate line and reboot.

That worked wonders for me!
[/QUOTE]

Speaking of which, what would the appropriate module for a Pentium Mobile processor be?

---

### Post by knappen on 2004-11-05
Have a look at this bug 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1444](https://bugzilla.ubuntu.com/show_bug.cgi?id=1444)

It talks about the problem with modules not being loaded automatically. This will probably be solved by the next release though.

Let me know if it helps.

---

### Post by discord on 2005-03-28
I am not having any luck with modprobe powernow-k7;

i get FATAL: Error inserting powernow_k7 (/lib/modules/2.6.8.1-3-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device

does powernow work with all athalonXP processors or just the mobile ones?

[QUOTE=knappen]I installed Ubuntu on my laptop with a AMD Mobile processor. Everything ran perfectly except the laptop got really hot and the battery life did not really have a life at all :-)

ubuntu-geek sugested I submit a bug, and I did. Problem is now solved.

There was one module that I needed to get the CPU frequency scaling to work that was not loaded. So if there is anyone out there with a really hot laptop using the AMD Mobile processor this is the module you have to load

powernow-k7

Edit /etc/modules and add powernow-k7 on a seperate line and reboot.

That worked wonders for me!

We really need a seperate forum for laptops[/QUOTE]

---

### Post by Bartholomaeus on 2005-05-03
thanks a lot, it workes perfect.

---

### Post by knappen on 2005-05-04
Good to hear!

---

