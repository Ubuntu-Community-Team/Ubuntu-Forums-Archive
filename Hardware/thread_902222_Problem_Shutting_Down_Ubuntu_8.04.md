---
title: "Problem Shutting Down Ubuntu 8.04"
date: 2008-08-27
forum: Hardware
---

### Post by nikidinsey on 2008-08-27
Hi all, 

First post apols if this is in the wrong place.

I have a problem shutting down my laptop (Asus G1S) from Ubuntu Hardy.

Basically if I choose shutdown/restart etc. the OS will close every program leaving me with a working mouse pointer and the desktop background. After 30-60 seconds the fan starts going nuts and nothing else happens.

If I click Ctrl+Alt+Back the GUI will close and the machine will shutdown or restart as asked. 

Not that this is a major problem with the workaround mentioned, but would somebody know why this is happening? I'm pretty new to Ubuntu/Linux environments... Is there any logs or ways of watching what is happening during shutdown to see where the problem is?

thanks in advance

niks

---

### Post by nikidinsey on 2008-08-28
bump ftw?

---

### Post by sameerds on 2008-08-28
> **nikidinsey said:**
> bump ftw?

I think this a problem that is very difficult to figure out through just forum discussions. Like you said, the system successfully stops when you hit Ctrl+Alt+Backspace. That means the problem is with the display server, which is simply called "X" in Ubuntu. You should report this as a possible hardware-specific problem. Consult [this howto]("https://wiki.ubuntu.com/X/Reporting") for details. Notice that "X does not shutdown" is mentioned as a well-known problem in that howto!

---

### Post by nikidinsey on 2008-08-28
Thanks sameerds, that is exactly the type of link I was looking for. I'll review the logs and submit a report if required.

cheers

niks

---

