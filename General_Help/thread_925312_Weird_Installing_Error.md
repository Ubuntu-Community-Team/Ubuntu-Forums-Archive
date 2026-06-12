---
title: "Weird Installing Error"
date: 2008-09-20
forum: General Help
---

### Post by hasek522 on 2008-09-20
So I get this error every time I try to install anything on to my fresh ubuntu system. This includes trying to install updates or other peices of software.

Here is the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What can I do about this?  I have tried running the command it gives me but I am told I have to be in "super user" mode.  I am brand new to linux so forgive me if I am missing things that are blantantly obvious.

---

### Post by TheLions on 2008-09-20
> **hasek522 said:**
> So I get this error every time I try to install anything on to my fresh ubuntu system. This includes trying to install updates or other peices of software.

Here is the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What can I do about this?  I have tried running the command it gives me but I am told I have to be in "super user" mode.  I am brand new to linux so forgive me if I am missing things that are blantantly obvious.

to be a super-user user command ```
sudo <your_command>
``` or type ```
sudo su
``` and then your command eg ```
sudo dpkg --configure -a
```

---

