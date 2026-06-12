---
title: "Expert Needed, Dell XPS 1530"
date: 2008-08-21
forum: Hardware
---

### Post by FerociousTwig on 2008-08-21
Ok I am struggling with a lot of things. The first and hopefully simplest thing I need help with is my wireless internet. I have a dell wireless 1505 card (broadcom chipset). I have read maybe 10 different threads about broadcom fixes but I am reeeeeaaally new to linux. I installed it literally 3 days ago. So basically, my problem is that my wireless network does not auto-connect. When I go 'connect to other wireless network' and entire my info, i can connect maybe 1 out of 5 tries. My connection is WPA secure but that is not the problem I'm sure. If anyone could give me step by step directions to fix this I would be forever indebted to you. Also, if you need anymore information about my problem, paste a command you want me to run because I know almost nothing about linux yet. Thanks a ton \\:D/

---

### Post by pytheas22 on 2008-08-21
Please post the output of these commands:
```

lshw -C Network
dmesg | grep -e b43 -e bcm -e wl
lspci -nn | grep -i broadcom
uname -m
```

With that, we can give you easy instructions on how to fix the wireless.  I imagine that the problem is a flaky driver; there are other drivers that you can use instead that should be more stable.

---

