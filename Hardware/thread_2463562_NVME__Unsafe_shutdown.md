---
title: "NVME : Unsafe shutdown"
date: 2021-06-14
forum: Hardware
---

### Post by georgesgiralt on 2021-06-14
Hello All,
On my new laptop there is an NVME SSD drive (SAMSUNG MZALQ256HAJD-000L2).
This machine runs Ubuntu 20.04.2 LTS alongside Windows 10 Pro. 
On both OSes (I run 99.5% of the time Ubuntu) I do proper shutdown if I have to power off  the machine.
But the SMART subsystem give  :
    Unsafe Shutdowns:                   366
And this figure keeps increasing. 
So I've some questions :
What did I do wrong ? 
What is this parameter and what meaning does it have to a casual user ? (I can't find clear answer on the Internet...) 
Should I worry ? 
Many thanks in advance for your help and answer !
P.S. : I've checked the computer my wife use (running Ubuntu)  which has also an Intel NVME and there is also a big Unsafe Shutdown figure

---

### Post by tea for one on 2021-06-14
Interesting question - I wonder if it is connected to other operations where (or if) the power status is altered?

e.g. Suspend, Lock, Hibernate 

I also found this nugget:-

[https://community.intel.com/t5/Solid-State-Drives/SSD-Number-of-quot-Unsafe-Shutdowns-quot-increases-after-each/td-p/1205019](https://community.intel.com/t5/Solid-State-Drives/SSD-Number-of-quot-Unsafe-Shutdowns-quot-increases-after-each/td-p/1205019)

Currently, I have [COLOR="#0000FF"]42 Unsafe Shutdowns[/COLOR] using an Intel NUCi3 BEH board and a Kingston A2000 250GB nvme drive (Ubuntu 20.04 only)

Following your post, I'm going to keep an eye on it to see if it increases, although I'm not excessively perturbed.

As to your question [highlight]Should I worry?[/highlight] - Back up regularly is the best advice.

---

### Post by georgesgiralt on 2021-07-01
Hello all,
Yesterday, I booted the laptop under Windows 10 to make some software update. (I do it about once a month to keep my Windows current if I needed it.)
The computer was rebooted a couple of times (Windows...) and now the "Unsafe shutdown" parameter  is at 370 instead of the 366 it was before. 
As I've restarted my Ubuntu a lot (traveling) without any change in the parameter value and given it has gained 4 points when I used Windows, I guess there is a problem with Windows shutting down and not allowing the SSD to save it's state... 
So I bet we can safely ignore this value if only running Linux with NVME SSD...  Just guessing ;-)

---

