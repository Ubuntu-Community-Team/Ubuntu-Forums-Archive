---
title: "Problem with make :("
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by andrex316 on 2009-05-19
I'm still pretty new with ubuntu and I was trying to install a monitoring software following the instructions from this website:

[http://www.ubuntugeek.com/how-to-install-a-monitoring-system-pandorafms-20-in-ubuntu-804.html](http://www.ubuntugeek.com/how-to-install-a-monitoring-system-pandorafms-20-in-ubuntu-804.html)

when i got to the part that says "Run make", i type make in the terminal and get teh following error: "make: *** No targets specified and no makefile found.  Stop."

could someone help me by telling me what is the right command I have to type or if there's something else that needs installing before I can run make correctly.

Thanks in advance!

---

### Post by andrex316 on 2009-05-19
bump...doesn't anyone wanna help a n00b??

---

### Post by andrex316 on 2009-05-20
i've found out that I have spicify the path where the makefile is before make can work, so i did 

```
cd /home/username/trunk/pandora_server
```

[IMG]http://i43.tinypic.com/2vmy3bc.png[/IMG]

and then typed "make" and still got the same error message: "make: *** No targets specified and no makefile found. Stop."

then i typed "make Makefile.PL" and I got: "make: Nothing to be done for `Makefile.PL'"

is there something I'm still doing wrong?

---

