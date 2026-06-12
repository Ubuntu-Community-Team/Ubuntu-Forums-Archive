---
title: "hal-probe-volu"
date: 2009-02-16
forum: Hardware
---

### Post by scifo_dk on 2009-02-16
Hi People.

I've just bought a new laptop, and installed a dual-boot xp/ubuntu ibex.
But I found out, that when I boot up, the pc halts for 15 secs, just before the menus loads. I therefore made a bootchat, and seem to have found the problem "hal-probe-volu" that halts between 25-40 secs. (see enclosed .png)

So, I think I found the cause of the problem, now for the solution, and thats where you come in :)
Don't know how to correct this issue.

Link to specs:
[http://zepto.dk/Files/15_Specsheet_Mythos_A15_UK.pdf](http://zepto.dk/Files/15_Specsheet_Mythos_A15_UK.pdf)

---

### Post by scifo_dk on 2009-03-10
After a long search (and with a lot of help) I found the cause, and is posting it here, in case someone else discovers this problem.

It was caused by my graphics card not beeing supported by the current ubuntu version, causing it to think I have a Riva TNT2 card and serching for 8mb of ram on the card, which ofcause doesent excist. Due to that, I get the halt.

//Scifo

---

