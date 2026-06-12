---
title: "How do I test my keyboard KEYS (Alt key)"
date: 2009-07-06
forum: Hardware
---

### Post by master5o1 on 2009-07-06
How do I test if my keyboard keys detected when pressed --

My right Alt key isn't working and I want to know whether it is:

1. Hardware fail.
2. Software fail.

---

### Post by stinger30au on 2009-07-06
easy

im using firefox 3 and if i press 

ALT+T

the tools dialog box opens it has a _ under the letter t so it opens

if i press

 ALT+S

the web broswer history opens up cos the  s has a _ under it

hope this helps

---

### Post by master5o1 on 2009-07-06
My left alt key works fine, my right alt key doesn't.  I am wondering whether it is hardware or software related :|


Is there some way to tell whether it is hardware or software?

---

### Post by joq on 2012-11-10
I had a similar problem today, my down key stopped working. When googling revealed this question, I was disappointed that no one had answered it.

The simple solution is running `xev` in a terminal. If the key works an event will be received and printed; otherwise nothing.

---

