---
title: "Laptop monitor display ----&gt; flickers now &amp; then"
date: 2009-09-28
forum: Hardware
---

### Post by Ezipan on 2009-09-28
- My laptop display gets flickering now & then whenever I minimize/maximize windows or launching some applications. 

- It becomes also saturated with lines and solid colors for a while before it goes back normal.

A screenshot is attached.


Any clue?

---

### Post by senthilmuthiah on 2009-11-02
I have the same problem too - upgraded to Karmic koala, Lenovo Y500, intel video card.

---

### Post by gazorzos on 2009-11-03
Same problem, but it doesn't work again. eee pc 1101ha.
I have to panic shut down.

Display is not configured: refresh rate: 0hz, false resolution

---

### Post by fiamazo on 2009-11-03
> **gazorzos said:**
> Same problem, but it doesn't work again. eee pc 1101ha.
I have to panic shut down.

Display is not configured: refresh rate: 0hz, false resolution

Two things that solved the same issues on my own 1101ha

* Get the poulsbo drivers from like here 

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8182373&postcount=87](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8182373&postcount=87)


* Install the newest compat wireless, like here

[http://ubuntuforums.org/showpost.php?p=8195189&postcount=97](http://ubuntuforums.org/showpost.php?p=8195189&postcount=97)

Probably you did already the first part. The second part should be the critical part, because it seems that this bad X issue seems to be related to old/broken ath9k drivers. I installed also wicd instead of network-manager, but I dunno if this could be helpful.
Regards,
fiamazo

---

