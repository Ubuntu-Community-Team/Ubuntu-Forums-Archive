---
title: "Trusting type unknown"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by blane245 on 2009-08-06
I am trying to install wine on my Dell Mini that has Hardy installed. After putting the dweb in third party software and adding the athentication key, I can no longer start either the software or the synaptic manager. I am getting the following error:

E:Type 'Trusting' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read.

What's up?

---

### Post by Partyboi2 on 2009-08-06
Hi, looks like you need to fix up a sources.list entry around line 16. (the word 'trusting' is not meant to be their). Open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
``` if you need help fixing it.

---

### Post by blane245 on 2009-08-06
got it. thanx.

---

