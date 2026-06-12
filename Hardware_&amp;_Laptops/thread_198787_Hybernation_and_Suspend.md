---
title: "Hybernation and Suspend"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by mellon85 on 2006-06-17
I have a strange problem.
Previously (pre dapper) suspend didn't worked but hybernation did. No problem, the laptop was not fully supported.

Now (dapper) I can suspend but not hybernate.
If I suspend the laptop the audio device becomes busy and isn't possible to use.
The worst thing happends with hybernation! Lot's of times it doesn't reach the activation of X, and if does it crashes continuosly and i must reboot [since it doesn't let me to go to any terminal]. A many times the hybernation fails and must be request 2 or 3 times before it works.

What's happening? :confused: on which log i can find any information? :confused:

---

### Post by kreso on 2006-06-17
I've been experiencing the same troubles since the new kernel. Suspend now works (yay!) but when I resume, audio doesn't work.

Hibernate still works perfecly for me though.

---

### Post by mellon85 on 2006-06-26
I have manually installed the most recent version of laptop mode scripts (i found a debian of the lastest version) and now everything seems to work

---

