---
title: "100% cpu usage on Compaq presario 2500"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by chaf_nee on 2006-12-11
Hi there . this is my first post in this forum :) 

im an Ubuntu-lover and i have my Box already with Ubuntu. alas i have a problem with my Laptop on Ubuntu. everything instals fine and all, but the Laptop responds way too slow to any command. i saw through the gnome monitor that my cpu is always on 100% cpu usage even if i do nothing. I thought it was a hardware problem, but then, windows works just fine. and that makes me angry cause i want Ubuntu to rock, and not Redmonts OS

sorry for my bad english :P

my specs : 
Compaq presario 2504eu
768 MB RAM
40GB HDD
ATI IGP 345M shared memory (64MB)

any help would be apreciated :)

by the way, this Forum just rocks! never saw such a good Community

---

### Post by zgornel on 2006-12-11
Run in a terminal ```
ps aux
``` and see what process is consuming processor time (3'rd colum, percentage of processor).
Does it happen every time or seldomly?

---

