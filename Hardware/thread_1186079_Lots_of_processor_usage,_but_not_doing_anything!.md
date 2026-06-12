---
title: "Lots of processor usage, but not doing anything!"
date: 2009-06-13
forum: Hardware
---

### Post by mpc350 on 2009-06-13
Hi, 

I'm using Intrepid on a late model Lenovo Ideapad Y530 with a pentium dual core and 2gb ram.  Several times, I have noticed that the CPU load and memory usage jump up while the computer has been sitting idle for a while.  It's not like indexing or some other process just doing it's thing, this is consistent high cpu and memory usage with no applications open, and I can't kill this unless I restart. 


I included a screenshot of the system monitor as an attachment.  In short, the main users of resources when this happens are "dd", "klogd", and "syslogd".  I don't know what these processes are, and trying to kill them does not result in much.  

Any ideas?
Thanks in advance,
Matt

---

### Post by kidders on 2009-06-14
Hi there,

That sounds suspiciously like [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285"), but it should be fixed by now. Could you post the output of **uname -a**?

---

