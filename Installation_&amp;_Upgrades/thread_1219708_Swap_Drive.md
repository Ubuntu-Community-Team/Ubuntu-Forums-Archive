---
title: "Swap Drive?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2009-07-22
Do I have to Create A Swap Drive or File or whatever it is called. If So, How can I make one?

---

### Post by tommcd on 2009-07-22
The swap partition should have been created when you installed Ubuntu.
To see if you have a swap partition, open a terminal (applications > accessories > terminal) and run:
```
free -m
```
If you have a swap partition, it will look something like this:
```

bash-3.1$ free -m
             total       used       free     shared    buffers     cached
Mem:          2025       1763        262          0         30       1287
-/+ buffers/cache:        445       1580
Swap:          956          0        956
bash-3.1$ 

```
As long as you have enough RAM (at least 1GB) you don't strictly need a swap partition. It does not hurt, and it can be helpful, to have a small (256mb-1GB, depending on how much RAM you have) swap partition though.
If the output of your **free -m** shows that you have no swap, I can try to help you create one if you want.

---

### Post by dk06 on 2009-07-22
If not, 

[http://ubuntuforums.org/archive/index.php/t-265051.html](http://ubuntuforums.org/archive/index.php/t-265051.html)

---

