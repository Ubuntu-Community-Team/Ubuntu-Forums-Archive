---
title: "Only about 12mb of memory free out of 1gb?"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by strabes on 2007-05-10
I have attached a screenshot from the KInfoCenter which shows that there is only about 20mb free of the available 1gb of memory. It is pretty much always like this. The programs that I have open are firefox, konsole, KInfoCenter, kmix, konversation, gaim, and Amarok. I have also attached a screenshot from the Process Table of K System Guard showing the processes that are taking the most memory. Is this normal? Thanks for your help. I'm thinking of upgrading to two gigs of ram; would this help this "problem," make my system faster, or both? Thanks again.

---

### Post by ohgod on 2007-05-10
I wouldn't worry about it.  About half your ram is being used as disk cache, which is normal.  If another app needs some more memory, some of the ram used by the disk cache will automatically be freed up for it.  

You can mostly consider the ram used as disk cache to be free.  It'll become available if anything needs it.  So I'd say you really don't need that extra gig of ram.

---

### Post by rockdon on 2007-05-10
This is more of an understanding issue for how linux handles memory management. While it may seem that most of your RAM is being used up, and that having 20mb free out of 1gb is a bad thing, its the way linux does things. Linux will use available memory to cache data for quick access. Doing so can have great results with respect to read speed. In your attached picture, it shows how much is being used by programs, and how much is simply cached data. 

What speed issues are you experiencing?

---

### Post by strabes on 2007-05-10
I'm not really experiencing any speed issues, I just wanted to make my computer perform faster and I thought that doubling the RAM would help. Will it not?

---

### Post by Tanker Bob on 2007-05-10
It depends on your usage characteristics.  More disk cache will make repeat loading of programs and data way faster.  More RAM will speed up video editing, large database manipulation, and other memory-intensive tasks.  If you run large programs or programs with large data sets, more RAM will delay swapping which will increase execution speed.  It isn't like Windows, though, which hogs RAM and CPU time for tons of services you'll never use.  Windows ALWAYS needs more RAM, but not so with Linux.

I recommend that you look at the Application Data usage on initial startup.  If it's at or below 30%, you're probably fine unless you do heavy multimedia editing.  Also check your swap usage after about a day's normal use.  If it's 5-10% or less, you're in good shape.

---

