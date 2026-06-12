---
title: "Can someone help me analyze my bootchart??"
date: 2008-11-15
forum: General Help
---

### Post by swoody on 2008-11-15
I installed bootchart to try and find out what is slowing down my system on startup. I don't really know anything about the info, so I'd like to know if you can tell me what are some things I can do to speed up my boot. I've included the graph below. Thanks in advance!! :D

---

### Post by swoody on 2008-11-17
Any ideas anybody?

---

### Post by starcannon on 2008-11-17
I'm still an egg on these issues, but I'd say from first blush its possible that wpa supplicant is having a hard time getting connected to your wifi access point. Perhaps try a couple of boots with the wifi card disabled and see if thats correct?

---

### Post by starcannon on 2008-11-17
Looking again I see a lot of zombie action on udevd, I would revise my first newb assumption and start going down that rabbit hole instead if my suggestion leads no where; indeed, as I now suspect it will.

Perhaps unplug all non-essential to the booting of the computer peripherals, and one at a time plug and reboot till you find the offender (i'm sure theres a faster way, but I don't know it yet).

GL and hang in there, I'll help you throw spaghetti at the wall till someone who knows more comes along.

---

### Post by starcannon on 2008-11-17
Concerning udevd I found this post, I'll dig around some more, but am getting sleepy...
[http://ubuntuforums.org/archive/index.php/t-859370.html](http://ubuntuforums.org/archive/index.php/t-859370.html)

Okay one more post, this one seems to really discuss some ideas to solve udevd going bonkers:
[http://www.uluga.ubuntuforums.org/showthread.php?t=801266](http://www.uluga.ubuntuforums.org/showthread.php?t=801266)

GL and keep us posted, I'm curious to find out what it is, evms perhaps?

---

### Post by swoody on 2008-11-17
> **starcannon said:**
> Perhaps try a couple of boots with the wifi card disabled and see if thats correct?

I tried this, and my boot time went up to 35 secs? I reenabled it, and now it's still up at 33 seconds :(

> **starcannon said:**
> Perhaps unplug all non-essential to the booting of the computer peripherals...

I don't have anything plugged in besides the charger (laptop).

> **starcannon said:**
> Concerning udevd...
[http://ubuntuforums.org/archive/index.php/t-859370.html](http://ubuntuforums.org/archive/index.php/t-859370.html)

...udevd going bonkers:
[url]http://www.uluga.ubuntuforums.org/showthread.php?t=801266[/url

udevd's not even registering on my conky or in System Monitor. All my stats and cpu usage is normal as well

---

