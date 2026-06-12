---
title: "[SOLVED] sniff on a program?"
date: 2008-11-19
forum: General Help
---

### Post by StOoZ on 2008-11-19
is it possible to check to which IP's a particular program is associated / connected to?

for example , if I have a program named "XXX" , and its running in the background , I would like to know to which IP's its being connected / transmit data at a particular time...
any terminal command / way to do it?

---

### Post by whitegourd on 2008-11-19
Have you tried using wireshark?  If you sniff the current IP that your system is on, it may give you some idea as to what other IP it's connecting/trasmitting to.

sudo apt-get install wireshark

---

### Post by StOoZ on 2008-11-21
cool thanks,

---

