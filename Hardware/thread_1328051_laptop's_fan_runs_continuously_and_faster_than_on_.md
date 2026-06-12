---
title: "laptop's fan runs continuously and faster than on windows!"
date: 2009-11-16
forum: Hardware
---

### Post by creatxr on 2009-11-16
laptop's fan runs continuously and faster than on windows!
but i found that the cpu runs only about 30% speed total in the system monitor.
why?
how to?
thanks.
---------------------------------
shapr's pc-mw70j
intel(R) pentium(R) M processor 1.73G Hz
ubuntu 9.10

---

### Post by yossell on 2009-11-16
When I first installed Ubuntu, I had exactly the same issues with my laptop. Moreover, battery life
was considerably shorter. In terms of power, Vanilla Ubuntu seemed to be more demanding than windows on the cpu .

I found the program powertop to make a *huge* difference. See

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

I run it as root from a terminal and just follow its suggestions and continue from there. Battery life and fan noise are now back to windows levels. 

I've also found that, by also running a minimal openbox session, my laptop lasts longer and is quieter than under windows - but you may not want to go that far.

Hope it works out for you

yossell

---

