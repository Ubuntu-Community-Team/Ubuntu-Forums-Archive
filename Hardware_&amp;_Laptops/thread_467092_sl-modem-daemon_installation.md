---
title: "sl-modem-daemon installation"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by cerebrosus on 2007-06-07
hi guyz,

everytime i try to install installation  with the command line to make my modem workable the command line gives me an error messege which is :-
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

the command i use is :-
butcher@butcher:/$ sudo apt-get install sl-modem-daemon

So, could you help me please

---

### Post by t4thfavor on 2007-06-07
Looks like there is another process running with a lock on that directory. Possibly synaptic, apttitude, or an update session. 

try a ps -ef and look for the offending process.

---

