---
title: "kacpid gobbling cpu"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by king20878 on 2005-02-25
I'm setting up Ubuntu on a laptop for a friend.  Everything is going nicely, except I've got a problem with a momentary pause about every seven seconds or so.  The mouse freezes, sound drops, even the harddrive pauses.  From what I can see in tops, it looks like kacpid is momentarily hogging the cpu (90% plus).  If I renice it to 19, everything runs smoothly.  

Anyone know a permanent fix for this?

or 

How do I set it up so that kacpid launches with a low priority initially?

Thanks for any help!

---

### Post by dbouwer on 2007-01-10
BUMP!!

I am having the same problem, lowering the priority of the process works perfectly?

There must be a way af starting the process with another priority level???

---

### Post by luka1983 on 2007-11-07
Do you have nvidia drivers installed? - some people guess that this is the cause.

As for solution I would really like to have a good way of fixing this without turning acpi off or renice for that matter. Btw you might want to add renice  to /etc/rc.locale

---

### Post by king20878 on 2007-11-07
Thanks for your reply luka.  I know longer have this laptop.  I really appreciate your participation in the forum though. Keep it up for the good of the community!  :)

---

