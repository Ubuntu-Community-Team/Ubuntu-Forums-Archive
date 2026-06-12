---
title: "cpufreqd does not start after boot"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by pdietric on 2006-11-18
Hello to everybody,

Yesterday, I replaced powernowd with spufreq on my laptop (T60 Dualcore) using apt-get. It worked without any problems until I rebooted. The daemon failed to start (/var/log/boot says just that). Doing /etc/init.d/cpufreqd start manually also fails.
I also noticed that the directory /sys/devices/system/cpu/cpu0/cpufreq/ does not exist anymore. 
I then reinstalled powernowd (apt consequently removes cpufreqd), it started without any complaints. Next I reinstalled cpufreqd (apt removes powernowd again). Now cpufreqd starts up flawlessly.
Someone suggested that this behavior might have something to do with cpufred's init script ( [http://www.ubuntuforums.org/showthread.php?t=67714&highlight=cpufreqd](http://www.ubuntuforums.org/showthread.php?t=67714&highlight=cpufreqd) ). On the one hand it seems to make sense but on the other hand I can't believe that this "bug" should not have been discovered and fixed lonhttp://www.ubuntuforums.org/showthread.php?t=67714&highlight=cpufreqdg ago. It also seems that not everyone is having this kind of problem.

It would be nice if someone could help me with this.

Thank you,

Peter

---

### Post by zcik on 2007-02-15
I had exactly the same problem. After following the link from your post and googling a little bit I found out that installing cpufreqd instead of powernowd somehow mess up loading of the modules. I added **powernow-k8** (I use Athlon64) and **cpufreq_ondemand** (depends which governor you use) into my /etc/modules and it works :)
A basic list of modules for various processors: [http://www.damnsmalllinux.org/dsl-n/f/viewpost/1666.html](http://www.damnsmalllinux.org/dsl-n/f/viewpost/1666.html) (the second post)

---

### Post by compwiz18 on 2007-02-15
Yeah, I had the same problem, same solution.  Maybe I'll file a bug report somewhere, this should be fixed.

---

### Post by Finch75 on 2007-07-04
*BUMP*

I'd just like to mention that I ran into the same problem yesterday on an Athlon X2 with a 64 bit (K)Ubuntu on a new Feisty Fawn install.

I'm new to Ubuntu and don't know what to do with bugs, but could somebody please file a bug report or tell me where that can be done? This is clearly a bug in the cpufreqd configuration in the repository and I think it should've been fixed in the last 8 (edit: **22**!) months! If not that, at least it should've been fixed in the new release 7.04.
If not that, it should at least be fixed for 7.10! I don't get it... if I understood this correctly, NOBODY can install cpufreqd from the repository on a new AMD architecture (Opteron, Athlon64) ... why doesn't anybody discover and fix this?

This has cost me a lot of time and was very frustrating :-(
(I have not fixed it yet, but this description here in the forum is *exactly* the problem I experienced so I expect it to be the same fix...)

Finch

---

