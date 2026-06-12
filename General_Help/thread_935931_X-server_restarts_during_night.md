---
title: "X-server restarts during night"
date: 2008-10-02
forum: General Help
---

### Post by sufslnd on 2008-10-02
Couple of days in a row now my x has crashed during night. I have to log in again each morning. This is pretty annoing since I have programs and **** running over night.

dmesg does not give me anything. Somewhere else I need to look?

---

### Post by Yellow Pasque on 2008-10-02
/var/log/Xorg.0.log  ?

---

### Post by sufslnd on 2008-10-02
uhm, there is no timestamps so I have no clue what is relevant and not. Have to check right after it crashes then..

---

### Post by ipburbank on 2008-12-27
Anyone? I'm having this problem too.

I got a new computer a few months ago, and all versions of ubuntu that I run (studio, and normal, also ultimate 2.0) were fine on my old computer, but now restart during the night presenting me with a login window in the morning. Now this isn't a problem most of the time, but sometimes in ubuntu studio I have renders going on and stuff that take a few days... that can't get past one.

~I really could use some help here, Istvan.

---

### Post by hal8000 on 2008-12-27
The problem with any (unattended) crash is knowing what caused it.
dmesg looks at /var/log/messages, the previous message will be archived and called /var/log/dmesg.0
Looking at this file and timestamp will give you some indication of when the system crashed.

Discovering what caused this, is a little trickier, you need to know what was running and if network services were running or have an impact on your problem. The easy way is to turn off your router or unplug ethernet lead.

If its not network related then you need to know whats running on your system and what can be turned off to eliminate this. Running gnome-monitor, qps, or even ps -aux in a terminal will show running processes.

Running only whats necessary will take time, so, its its unattended disable visual effects like compiz etc.
It could be hardware related, maybe system is getting hot? but if the problem only happened in the current ubuntu release, then look through the software youre running.
In addition, disable any startup services you dont need, e.g. if you dont have a blue tooth device disable blue tooth etc
Hope that helps.

---

### Post by ipburbank on 2008-12-27
I don't think it is overheating, tho it could be. I will try all of that tomorrow, at which time my computer might have restarted overnight.

I looked at some of the logs last time, and I didn't find anything to bad in them, just the usual. I will post what I find.


BTW, it was on my old computer that I was running the old versions, so that shouldn't count for much.

---

### Post by lswb on 2008-12-27
> **Temüjin said:**
> /var/log/Xorg.0.log  ?


Actually, Xorg.0.log.old will be the log for display 0 from the previous X session, presumably the one that crashed.

---

### Post by ipburbank on 2009-01-12
attached is my log, but I can't find anything, but then again I don't know what I'm looking for. If someone could take a look and see if there is anything wrong it would much appreciated!

~it is really annoying to have to start stuff over when my computer can't make it thru the night - Istvan.

---

### Post by ipburbank on 2009-03-11
It just happened again, but this time not at night... 

A common theme is I am using Blender 3D to render, but I don't often have these problems. It might be a bug with blender, I will have to try some other tests. But please, check that log!

---

