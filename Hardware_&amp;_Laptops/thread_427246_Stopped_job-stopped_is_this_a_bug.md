---
title: "Stopped: job-stopped is this a bug?"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by clpc on 2007-04-29
With a fresh install of either edgy or feisty the first thing I do is to add my Alps MD-2010 or my Citizen Printiva600C, the drivers are available in the 'Add New Printer' and I select LPT #1.

When I try to print a test page the printer jobs just shows the status as Stopped: job-stopped.

I get the same result no matter what application I try to print from.
I have checked that I am a member of the lpadmin group.

This is driving me totally crazy.

Does anyone have any idea of what is wrong or what I am doing wrong?

:(

---

### Post by zorkerz on 2007-04-29
Have you found anyone else who has this problem or has theirs working. If it says it is installing drivers for your printer and they do not work it is definitely a bug. You could report it in launchpad, well first check to see if there is anything similar.
I used to have the same problem with my pixma ip1500 it was a pain for sure.
good luck

---

### Post by walding on 2007-04-30
Hi,

I am having the same problem.  I have (apparently) successfully install the Gutenburg driver for my Canon iP4000, and get the same job-stopped error every time.
Edgy had my printer listed in the Canon list.  Feisty does not.  Is there a reason for that (is it linked to this problem?)

AW

---

### Post by zorkerz on 2007-04-30
possibly they mislabeled it in edgy or thought it worked when it did not. I would imaagine they are somewhat related a bug on the issue would be good.

---

### Post by walding on 2007-05-01
Mine definitely worked in Edgy (from day one until I upgraded).  
Currently regretting upgrading to Feisty as I really need my printer...

I'm posted a Launchpad bug.  My first one, so hope I've done it right.

---

### Post by zorkerz on 2007-05-01
please toss a link for the bug so we can look at it.

---

### Post by walding on 2007-05-01
ah - yes...

[https://bugs.launchpad.net/ubuntu/+bug/111320](https://bugs.launchpad.net/ubuntu/+bug/111320)

---

### Post by Arjunanda on 2007-05-10
I am having the same problem with Canon LBP 4U printer. The error was occurring with cjet (recommended) driver. With the instructions given in the bug report [https://bugs.launchpad.net/ubuntu/+bug/111320](https://bugs.launchpad.net/ubuntu/+bug/111320) , I tried lbp8 driver and it worked. I have been using the printer (auto-detected) with cjet driver without any problems in dapper. Now having a fresh install of Feisty and I was not able to print until found these tips from here.

---

