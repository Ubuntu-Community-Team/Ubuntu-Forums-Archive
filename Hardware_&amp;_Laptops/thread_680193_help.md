---
title: "help"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by redhead1811 on 2008-01-27
when i go to install software in synaptic package manager i get this
E; dpkg was interupted

please help

---

### Post by taurus on 2008-01-27
Close down synaptic.  Then, open a terminal, Applications -> Accessories -> Terminal, and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
And if there is an error message, post the whole thing here and from what command.

---

### Post by redhead1811 on 2008-01-27
ok that worked but it said i have 1 broken filter what do i do

---

### Post by taurus on 2008-01-27
Can you post the exact error message?  It's kind of hard to tell you how to fix it since I am not sure what's wrong with it.

---

