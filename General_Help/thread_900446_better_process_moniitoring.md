---
title: "better process moniitoring"
date: 2008-08-25
forum: General Help
---

### Post by lduperval on 2008-08-25
Hi,

I am looking at the systme monitoring tool and is says that one of my CPUs is at 60% and the other is at 20%. Yet when I look at 'top' or the process list in the gnome system monitor application, I have no processes running at more than 6% CPU. Both report that I have a two or three of them running between 3 and 6% CPU, nothing to explain hy I have 60% and 20%.

Are there other process monitoring tools that I should consider using when I want to find out what is taskin my CPU?

Thanks,

L

P.S. I'm running Hardy.

---

### Post by Skorzen on 2008-08-25
Try [htop](http://htop.sourceforge.net/).
```
sudo apt-get install htop
```

---

### Post by bthoward on 2008-08-25
Under processes makes sure you have selected show all (or something like that).  But htop is a pretty good app.  But hell so is top.

---

### Post by lduperval on 2008-08-25
I installed htop. When things go nuts again, I'll try them both to see what's happening.

Thanks,

L

---

### Post by markseger on 2009-06-01
I'd try collectl and look at the expanded CPU stats which include things like time spent processing hard/soft interrupts.  It mat then also be possible to correlate the times of the CPU peaks with which programs were running at the same time.  While I can't speak of how other tools report CPU, I do know of some that include 'iowait' with the CPU load which is flat wrong as it's NOT real CPU time.
-mark

---

