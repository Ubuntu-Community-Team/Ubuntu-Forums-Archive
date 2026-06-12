---
title: "Dell Inspiron 1520 DellFand"
date: 2009-03-24
forum: Hardware
---

### Post by SumX on 2009-03-24
Hello everyone. I really hope you can help me solve my problem. I Have a Dell inspiron 1520 , Core 2 Duo 2.0Ghz, 2Gb RAM, Nvidia 8400M ... normal equipment. I installed Ubuntu 7.10 and my fans weren't working, so with a little GoogleUp, i found a Daemon called Dellfand, i installed it and run it, and my fans started working... But... 

When the Fan goes to Medium Speed, it accelerates very quick for 2 secs and then lowers the speed... no matter if my "check temperature" time is set for 10 secs... it just goes up the speed for 2 secs, and lower speed, and instantly, repeats this untill the temperature goes down... my personal set is: Sudo Dellfand 1 10 37 42 47 ... i dont know what to do now. Please, can the fans just keep in a speed based on the temperature, but still ??... 

Please, i really hope someone can help me, doesn't matter if you recomend Re-Installing Ubuntu xD... 
Thx

---

### Post by qalasi on 2009-03-25
Try:

sudo killall -s SIGINT dellfand

I had the same problem because I found I had multiple instances of the daemon active, even if I had closed the terminal to terminate them...
Then you can read on the site that is not recommended terminating the daemon with any signal other than INT...

---

### Post by SumX on 2009-03-25
Sorry but im still with the problem... i did what you said and, for example, if i set the Medium and High temperature to 37 and 45, whtn temperature reachs 38, the fan turns on for 2 secs and goes off... 2 secs later it turns on aggain in Medium and keeps doing that...  i still have the same issue

---

