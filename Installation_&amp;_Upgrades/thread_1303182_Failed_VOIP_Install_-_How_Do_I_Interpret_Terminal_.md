---
title: "Failed VOIP Install - How Do I Interpret Terminal Output"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by cat2005 on 2009-10-27
I am trying to follow these instructions to install VOIP:

[http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install](http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install)

_When I input this into terminal:_

cd /usr/src ; wget [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile) ; make

_I get that:_

catprime@catcpu:~$ cd /usr/src ; wget [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile) ; make
--2009-10-27 22:43:48--  [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile)
Resolving [www.freeswitch.org]("http://www.freeswitch.org")... 216.82.231.69
Connecting to [www.freeswitch.org|216.82.231.69|:80]("http://www.freeswitch.org%7C216.82.231.69%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 614 [text/plain]
Makefile: Permission denied

Cannot write to `Makefile' (Permission denied).
make: *** No targets specified and no makefile found.  Stop.
catprime@catcpu:/usr/src$ 


**Obviously it failed, but how do I interpret the message?**

Thanks!

---

### Post by mr_steve on 2009-10-27
> **cat2005 said:**
> I am trying to follow these instructions to install VOIP:

[http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install](http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install)

_When I input this into terminal:_

cd /usr/src ; wget [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile) ; make

_I get that:_

catprime@catcpu:~$ cd /usr/src ; wget [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile) ; make
--2009-10-27 22:43:48--  [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile)
Resolving [www.freeswitch.org]("http://www.freeswitch.org")... 216.82.231.69
Connecting to [www.freeswitch.org|216.82.231.69|:80]("http://www.freeswitch.org%7C216.82.231.69%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 614 [text/plain]
Makefile: Permission denied

Cannot write to `Makefile' (Permission denied).
make: *** No targets specified and no makefile found.  Stop.
catprime@catcpu:/usr/src$ 


**Obviously it failed, but how do I interpret the message?**

Thanks!

The permission denied message is because you do not have permission to write to /usr/src. You can overcome this by instead doing
```
cd /usr/src
wget [http://www.freeswitch.org/eg/Makefile](http://www.freeswitch.org/eg/Makefile)
make
```**However** it is probably safer to download the file into a directory you do have permission to, perhaps creating a 'src' directory inside your home directory.

---

### Post by cat2005 on 2009-10-29
Thanks!

---

