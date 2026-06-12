---
title: "Over-current change on port 1?"
date: 2008-06-28
forum: Hardware
---

### Post by mrmagpie on 2008-06-28
Earlier today, I accidentally allowed the battery on my laptop to run down to the point that the computer shut itself down. When I realized what had happened and re-booted the laptop sometime later, I received this error message on boot-up

hub 1-0:1.0: over-current change on port 1
hub 4-0:1.0: over-current change on port 1

and now, naturally, the adapter for my wireless mouse no long functions. Should I simply allow the battery to recharge and the computer to cool down and then try again, or have I inadvertently killed my ports? :confused:

---

### Post by mrmagpie on 2008-06-28
Well, it's the next day. The internal battery is back to normal, but I'm still getting the same error on boot-up. Is there anything I can do to fix this? The laptop mouse really isn't cutting it.:(

---

### Post by jimv on 2008-06-28
I'm curious, do you get the error if you take the battery out and boot up with just the AC adapter plugged in?

---

### Post by zivagolee on 2008-07-02
Mind is doing this also.. nothing changed besides a few hardy updates.  I'm gonna try a different kernel...

---

### Post by podfish on 2009-03-15
I ran into the same issue, and had a real issue manifest itself--my hard drive enclosure was doing all kinds of nasty stuff trying to initialize the drive.  Luckily, it worked fine on another machine, or i might have written off the drive and/or the enclosure.  I knew it wasn't kernel, because it started thrashing the drive as soon as the computer started POSTing.  Some devices can handle the overvoltage that the machine is sending, some can't.  Mine can't, so it thrashes and sends the overvoltage notice back to the kernel, which the kernel kindly lets you know.  Windows would just freak out and make it sound like your drive was failed or something.

What I did to mitigate the issue was to use a powered USB hub.  No more messages, no overvoltage passthrough.  Don't have a non-powered hub to try it on.

---

