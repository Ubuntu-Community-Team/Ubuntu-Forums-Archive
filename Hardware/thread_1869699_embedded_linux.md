---
title: "embedded linux"
date: 2011-10-26
forum: Hardware
---

### Post by alimooghashang on 2011-10-26
Hi all
i have a RoBoard RB-110 single pc board
what i need is to make an embedded linux for it to run lightly and fast enough for me
please help me how to make a custom embedded linux for it which contains the drivers and programs i need
thanks in advance

---

### Post by diasf on 2011-10-26
Go to the manufacturer website. One quick visit to google and I found it, even got lucky.

---

### Post by alimooghashang on 2011-10-26
> **diasf said:**
> Go to the manufacturer website. One quick visit to google and I found it, even got lucky.
i need lighter than lubuntu ;)

---

### Post by diasf on 2011-10-26
Get lubuntu, make a custom kernel build disabling everything you don't need. If you need X, can't get lighter than that, at least that i know of. LXDE is astonishingly light.

And you can always enable a swap file on that SD card the board has... (swapon command)

---

### Post by alimooghashang on 2011-10-26
> **diasf said:**
> Get lubuntu, make a custom kernel build disabling everything you don't need. If you need X, can't get lighter than that, at least that i know of. LXDE is astonishingly light.

And you can always enable a swap file on that SD card the board has... (swapon command)
thanks
how can i make custom kernel?
the problem is this ;)

---

### Post by collisionystm on 2011-10-26
You can try using slax

[http://www.slax.org/](http://www.slax.org/)

---

### Post by diasf on 2011-10-26
google for "compiling custom kernel". You probably can cross compile it on any pc and pass to the board

---

