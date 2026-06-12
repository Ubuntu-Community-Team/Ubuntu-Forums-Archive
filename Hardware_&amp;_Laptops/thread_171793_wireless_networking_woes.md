---
title: "wireless networking woes"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by nickdr on 2006-05-07
i have a linksys WRT54G router attached to my moms computer, which is runnning windows xp home, my computer is upstairs and i dual boot with windows xp pro and ubuntu dapper drake flight 6, windows has no problems connecting to the metwork. i have my router using WEP protections, 128 bit, and my netowork card is the linksys wireless g one. i have spent some time now trying to connect to the network, but it won't even with all encryption turned off. how can i use the interent in ubuntu????
thanks for the help

---

### Post by monomaniacpat on 2006-05-07
Have you looked under network settings to check whether the card is installed?

Try entering:

```
iwconfig
```

And see if it gives a wireless extension.

If not, you'll most likely have to install the drivers. Good open source drivers can be found [here]("http://linux-wless.passys.nl/"). Just download the file and read the install file for instructions. Alternatively, use [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=81461&highlight=ndiswrapper-utils").

Let me know if you need any more help.

---

### Post by nickdr on 2006-05-07
yeah it is listed in the iwconfig

---

### Post by chettyk on 2006-05-07
You might want to take a look at the chapter on wireless networking in the Linux Network Administrator's Guide, Third Edition, published by O'Reilly. The chapter on wireless networking is, as it happens, freely accessible online at:
[http://www.oreilly.com/catalog/linag3/chapter/index.html](http://www.oreilly.com/catalog/linag3/chapter/index.html)

---

### Post by nickdr on 2006-05-07
is there reason though why it still isnt connecting even with no security??

---

