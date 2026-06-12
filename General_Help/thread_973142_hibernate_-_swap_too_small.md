---
title: "hibernate - swap too small"
date: 2008-11-06
forum: General Help
---

### Post by Lanie on 2008-11-06
I did search but these forums are hudge... 
Did install Ubuntu on my new Acer. I didn't know how to go with manual install so chosed automatic, but then last night when I wanted to hibernate, the screen did blink and message appear saying there is not enough free swap. How to make swap bigger and how big should it be to be able to hibernate? Ubuntu partition is 100gb but only 8gb is used and I have 2gb RAM. Also I dont know how to look how big is swap now, lol :P Need help with all this.

---

### Post by mindoms on 2008-11-06
open a terminal and run:
```

free -m
cat /proc/swaps

```
The first one tells you how much ram is installed, the second one the size of your swap partition(s)

In case you need to increase your swap, you will have to resize your swap partition, (or create another one) using gparted. You might have to install it first.
Make sure to backup all importand data first, as something *might* go wrong.

hth, stefan

---

### Post by geirha on 2008-11-06
To hibernate, your swap should be at least the same size as your RAM. When you hibernate, it copies the content of RAM to the swap filesystem, and copies it back when you resume.

---

