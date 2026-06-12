---
title: "big noise when shutting down the system (IBM)"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by amwus on 2007-05-09
Hi all ! 
I run ubuntu 7.04 on a laptop IBM Thinkpad R52 (1846-3WG). I've only one embarrassing problem. When i shut down the system, just before the computer turns off, the hard drive makes a big clacking sound. I don't know why ! In windows, the computer turned off very quietly. 

I uses ubuntu for a while now and i always had that problem... 

Do you think it's possible to fix that problem ?

Thank you very much !

Regards.

---

### Post by obviouslyshane on 2007-05-09
I have had Ubuntu 7.04 on my dell Inspiron 1505 since beta, it makes that noise every time i shut down too, but it isn't really all that loud. So far it hasn't caused any problems though. Not sure if theres a way to stop it...

---

### Post by Jingo on 2007-05-10
I had the same problem.
Its a kernel bug. It has workarounds.

See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

The solution is a script, which is run on every startup.

---

