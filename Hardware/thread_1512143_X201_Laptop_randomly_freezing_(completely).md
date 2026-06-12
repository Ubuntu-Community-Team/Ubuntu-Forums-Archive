---
title: "X201 Laptop randomly freezing (completely)"
date: 2010-06-17
forum: Hardware
---

### Post by jskulski on 2010-06-17
Hey all,

I finally got ubuntu 10.04 installed on my new x201 lenovo thinkpad.

I am experiencing complete locking of my system every so often. X freezes, I can't dump to a console (ctl+alt+f1-7) and i have sshd running and it does not respond once my system is locked up.

I thought it was related to my USB or external monitor, but those things were not in use several times when it has locked. 

I don't see anything weird in my syslog or messages. My kernel doesn't panic (no caps lock flashes). 

I haven't experienced this in windows, so I think its in ubuntu. I will try using windows more, to see if I experience the problem there. 

I am a programmer so I am comfortable with code and such and want to dig in and see what is happening. 

Is there anyone who is experiencing a similar problem? 
Can anyone point me to some documentation on debugging these types of issues? More logs I should check? Settings I can turn on to get to the bottom of this? 
 

Any help or direction would be appreciated!

Thanks,
Jon

---

### Post by Guitar John on 2010-06-17
Just a thought.  If you have an internet connection on that computer, try doing an update.  I had a couple of lock-ups on a clean install that went away after updating.

---

### Post by jskulski on 2010-06-24
> **Guitar John said:**
> Just a thought.  If you have an internet connection on that computer, try doing an update.  I had a couple of lock-ups on a clean install that went away after updating.

I am fully up to date, thanks though.

---

### Post by t.rain on 2010-08-03
hi all,

i do have the same problem here with my x201, running kubuntu 10.4

I never experienced a freeze when running undocked (as far as i can remember), but experience a freezing machine once or twice a day when running docked and connected to an external monitor.

ANY help is appreciated, as this really is annoying.

My Kernel version: 2.6.32-24-generic

thanks a lot,

---

### Post by utilitytrack on 2010-08-03
to **jskulski**

Hello, post here [FONT=Courier New]uname -r [/FONT]and [FONT=Courier New]free -m[/FONT]

> I am a programmer


That's good :) Therefore see [https://bugzilla.kernel.org/show_bug.cgi?id=12309](https://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

### Post by t.rain on 2010-08-09
okay,

thanks for your reply, here we go:

```

uname -r
2.6.32-24-generic

free -m
             total       used       free     shared    buffers     cached
Mem:          3761       2223       1537          0         73       1062
-/+ buffers/cache:       1087       2674
Swap:            0          0          0

```

i have the feeling that sometimes it is related with Chromium (5.0.375.99 (51029) Ubuntu 10.04). At least when i close chromium i can -- in some cases -- prevent a total freeze...

again, any help appreciated!
T

---

