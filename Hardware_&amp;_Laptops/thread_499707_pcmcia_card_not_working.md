---
title: "pcmcia card not working"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by jflash on 2007-07-12
i just installed ubuntu 7.04 from an alternate install cd (couldn't get graphical version to work) on a secondhand dell inspiron 1000. during and after installation, it picked up a wireless connection (which i am getting using a dell wireless 1350 pc card that i assume came with the computer. However, it doesn't appear to pick up the network, and neither the power or link light comes on. Any thoughts? If it makes any difference, I am leaving town tomorrow night, and would like to get this resolved before i leave. Thanks!

EDIT: The card is 802.11 b/g, and the newtwork is b. The card worked under XP Pro, just not Ubuntu.

---

### Post by jflash on 2007-07-13
*bump* anybody?

---

### Post by ugm6hr on 2007-07-13
Check the output from:
```
lspci
```

If this lists Broadcom 4306 as a Network / Ethernet Controller, then there are a number of potential solutions:
Maybe start here:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

