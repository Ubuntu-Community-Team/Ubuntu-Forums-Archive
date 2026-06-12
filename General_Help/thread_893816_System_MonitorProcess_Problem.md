---
title: "System Monitor/Process Problem"
date: 2008-08-18
forum: General Help
---

### Post by Arsaine on 2008-08-18
I'm using Linux Mint Elyssa with GNOME, already posted in my 'native' :p forum, but I'm posting here too because I'm desperate.

So, booted Elyssa, opened Pidgin and Firefox 3. Shortly after that I noticed a major slowdown so I opened System Monitor to see what was wrong. Unpleasant surprise. A process named 'sleep' is shown running 3 times, when I try to select it, I can't because it just bounces off, disappears from the list, I don't know what. What's more, I can't select any other process because the same happens to it, and all processes are marked as 'sleeping' though they're obviously not. Then I leave it for a while, and a process with no name at all (!?) owned by root shows up and again, same story, can't do a thing to it. Resources tab shows memory usage of 50% and growing, CPU's going wild like I'm playing Mass Effect and Crysis at the same time...and the only thing opened is Pidgin.

Tried restart, logging as a different user, turning some services off...nothing helps. I don't even know what the problem is. Please, help me, it's driving me crazy and it's almost impossible to work in Elyssa now.
Thank you very much.

---

### Post by mikewhatever on 2008-08-18
I heard there were security issues of some kind with Mint. Have you installed anything from untrusted sources? A screenshot of your processes or top output would be nice.

---

### Post by Arsaine on 2008-08-18
> **mikewhatever said:**
> I heard there were security issues of some kind with Mint. Have you installed anything from untrusted sources? A screenshot of your processes or top output would be nice.


Server was hacked, yes, but it did not affect our Software Portal, and the trojan affected only Windows users, as far as I know. I have not installed anything recently, that's why I'm so confused about this --I have no idea why it's happening. 

Here's the screenshot...observe the evil nameless process.
[IMG]http://i38.tinypic.com/21bvsir.png[/IMG]

---

### Post by Arsaine on 2008-08-18
The last thing I installed was an update containing this:
python-sip4
python-qt4
python-qt4-common

---

### Post by Arsaine on 2008-08-18
Things are just getting weirder...and still no help :(

[IMG]http://i35.tinypic.com/2q9l7a8.png[/IMG]

---

### Post by cariboo on 2008-08-19
Could run in a terminal:

```
ps aux
```

and post the output in your next post.

this does the same thing as system monitor except its faster and a little more concise

Jim

---

### Post by mikewhatever on 2008-08-19
I've no idea what's wrong there, but those nameless processes look suspicious. Perhaps they are supposed to be there, can't tell, never used Mint. Also, where's the CPU load?

---

### Post by atx on 2011-03-13
Okay I figured it out! At least on my system.
Using: "ps -eopid,cmd,user,ppid | sed /\\[/d"
I've managed to get some usefull output. The gnome system monitor didn't managed to gather the process information. These disapearing "root" process were not root processes at all. It was "sleep 0.1" called by "bash /usr/share/playonlinux", so i guess it related to playonlinux and not to Ubuntu. Maybe its a bug.
Also its, quiet anyoing that the gnome system monitor produced this faulty output...

cheers!

---

