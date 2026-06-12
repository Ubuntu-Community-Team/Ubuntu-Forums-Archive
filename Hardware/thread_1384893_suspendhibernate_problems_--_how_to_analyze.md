---
title: "suspend/hibernate problems -- how to analyze?"
date: 2010-01-18
forum: Hardware
---

### Post by equaeghe on 2010-01-18
Hi,

I have (k)ubuntu 9.10 32bit on a Dell Latitude D620.
Previously (same install), I could hibernate and suspend.
In the meantime, only software installation and updates have taken place.
Now suspend/hibernate do not work anymore, meaning that nothing happens when clicking on the suspend or hibernate buttons in the logout/shutdown dialog.

I tried using pmi (command line utility), but that doesn't work either: "pmi action hibernate" gives
```

method return sender=:1.2 -> dest=:1.50 reply_serial=2
   int32 1
```

How do I further diagnose/analyze this problem, so as to be able to resolve it?

---

### Post by Klegger on 2010-01-18
I want to second this post as very important: how to analyze. Obviously everybody has a different hardware setup, so solving it one setup at a time means people have to start from scratch every time. 


My own problem: 
I have a desktop machine that does not suspend. When I hit suspend, it actually shuts off the monitor and seems to go into suspend, but then the cooling fan on the CPU hits maximum intensity and I'm unable to resume operation of the machine without turning it off completely and then turning it back on. 

Being able to investigate every piece of the chain of components involved here would be an immense help not only to resolving this issue but being able to solve similar ones in the future. 

Thanks in advance to any respondents!

---

