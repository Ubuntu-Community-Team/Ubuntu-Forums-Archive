---
title: "Acer Aspire One 722 Random Shutdown (overheating?)"
date: 2012-02-19
forum: Hardware
---

### Post by schruthensis on 2012-02-19
Hi,

I'm running Ubuntu 10.10 (2.6.35-32-generic) on an Acer Aspire One 722 laptop I bought for cheap at Costco 3.5 months ago. It's worked great for me for about 3 months, no problems...  

But now suddenly it's shutting down randomly (with a loud "click") and seemingly independently of which applications I'm running (although perhaps it could have something to do with video intensive apps like flash or adobe air). Also, their is nothing suggestive in the logs: neither /var/log/messages or /var/log/syslog show anything just before or after the crash.

This is a dual boot with windows 7 which doesn't appear to have this issue (I can boot right back into that and things seem to work fine but I don't spend enough time in windows to rule out a strict hardware problem).  

I ran across [a blog post that suggested that I uninstall my proprietary ATI drivers]("http://cosmicace.blogspot.com/2011/02/ubuntu-1010-randomly-shutdown-solution.html") but this didn't solve the problem. 

At first I thought it was related to a package update (firefox? chrome?) but I'm starting to think it's hardware related: 

-Perhaps my fan has gone bad or is clogged up? 
-Could it be the bit of salt water that splashed onto it a month ago that's only now manifesting? 
-Is it related to my power supply or battery? 

Other models of Acer laptops have had this issue:
[techsupportforum.com acer aspire 5315 random shutdown]("http://www.techsupportforum.com/forums/f108/acer-aspire-5315-random-shutdown-overheat-549572.html")

I've tried installing lm_sensors but it couldn't detect any sensors on my device.
([linuxquestions.org "ubuntu laptop randomly shuts off"]("http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-laptop-randomly-shuts-off-908027/"))

I'm hesitant to poke around inside because of how new it is. But should to rule out the fan possibility.

Any ideas?

Thanks

---

### Post by wolfen69 on 2012-02-19
> **schruthensis said:**
> 


-Perhaps my fan has gone bad or is clogged up? 
-Could it be the bit of salt water that splashed onto it a month ago that's only now manifesting? 
-Is it related to my power supply or battery? 


It *could* be any of those things. But I would boot into windows and stay there for a while and do some cpu intensive things to see if it is a hardware issue.

---

### Post by schruthensis on 2012-02-25
Well I finally talked with my sysadmin office-mate who convinced me to run memtest86 again (I had run it earlier but didn't get a chance to see the results as it had shut off by the time I woke up in the next morning)...  memtest kept failing and random points.   The strange thing is that it never crashed in windows 7 (even when using the prime95 mixed stress test!) 

I opened up the machine to look around and sure enough the fan was running just fine. (btw: one only needs to remove a *single* screw and then slide the back panel off this thing: I over-dismantled mine )  I never did find a pattern with where exactly the memory was failing but after picking up a $30 replacement stick at radio shack that day, the problem hasn't resurfaced in days now after intensive use (including a full memtest86 run!).

So I think I've solved it.:D

BTW: the bad memmory was Hynix:
[http://www.amazon.com/Hynix-PC3-10600-204-Pin-Laptop-SODIMM/dp/B004K4IULS/](http://www.amazon.com/Hynix-PC3-10600-204-Pin-Laptop-SODIMM/dp/B004K4IULS/)
it's one of the cheaper brands on amazon (only $5...)

---

