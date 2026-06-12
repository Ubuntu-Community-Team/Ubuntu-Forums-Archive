---
title: "Ran fsck and now GDM fails"
date: 2008-11-20
forum: General Help
---

### Post by Spitting Crows on 2008-11-20
I've got a Lenovo Y510 laptop and have been running both vista (yech) and Hardy on different partitions.  Hardy is on ext3.  Anyway, I'm not super knowledgeable, but am always learning and have been running Ubuntu for about a year.  

My computer has issues awakening from sleep mode when I'm running Ubuntu (hope that's helpful).  The other night, I ran the toolbar updates and among the updates I was offered was the login screen (I noted this as updates flew by).  I put the computer to sleep so I wouldn't leave my desktop settings and so I wouldn't have to listen to it all night.

Next day, I tried to turn it on, it got to the first Ubuntu login process bar and then, when it should've shown the signin screen, gave me errors and suggested I run fsck (I don't remember the errors, I just figured I'd follow the suggestions).  I "yes"'d all the ones that popped up and then restarted.  Now, the linux won't start up.  Here's an excerpt of what I see before it gives me a tty login option:
> ...
/usr/bin/cupsd:error while loading shared libraries: libdbus-1.so.3: cannot dynamically load executable
...

> 
...
segmentation fault
...

> ...
usr/bin/dhcdbd: error while loading shared libraries: libdbus-1.so.3: cannot dynamically load executable
   *can't start Hardware abstraction layer - please ensure dbus is running
   * Starting GNOME Display Manager...                [Fail]

and then it lets me login with tty.

I'm not sure what to do and how to do it.  My primary partition is vista, it came with the computer so it stays..., I'd be into reinstalling ubuntu, but I don't want to lose the data I had on that partition.  Ideas?

---

### Post by Spitting Crows on 2008-11-23
I've been running for a week without linux, and I don't think I can stand Vista anymore (it's not even consistent, say, with internet connectibility)...  Anyone?  Help!?!?!

---

### Post by Spitting Crows on 2008-11-23
I've been running for a week without linux, and I don't think I can stand Vista anymore (it's not even consistent, say, with internet connectibility)...  Anyone?  Help!?!?!

---

