---
title: "Bootup"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by danip on 2005-04-25
How long is everyones computer taking to boot up?  Mine takes at least 2 minutes to boot up which I think is very slow.  I already installed the 686 kernel but that did not speed up much.  If there are other people out there whos computers boot up faster what can I do to improve mine?

---

### Post by GrumpySmurf on 2005-04-26
I haven't timed my boot up, but it seems fine.  To improve boot time, you will need to disable some of the startup services.  Unless you know what you're doing, you probably shouldn't mess with these, however.  Startup services run from /etc/rc2.d/ when the system initializes runlevel 2 (default runlevel on Ubuntu).  Files in this directory are symbolic links to scripts in /etc/init.d/.  Editting the runlevel services is an intermediate to expert level task.  If you can't figure out how to manage the scripts, then you shouldn't be making changes.  That said, here's a few of the services I see that I'd disable one of these days.

/etc/rc2.d/...
S14ppp
S20rsync
S25mdadm

Looks like everything else is pretty much necessary.  There's other start scripts in /etc/rcS.d/ but I wouldn't touch anything in there, unless you absolutely know what you're doing.

---

