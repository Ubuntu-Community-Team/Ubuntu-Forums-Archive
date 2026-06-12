---
title: "Cardreader does not work."
date: 2009-04-30
forum: Hardware
---

### Post by K. Hendrik on 2009-04-30
Hi,
I've got a Problem with my Internal Cardreader of my Acer Aspire 6935 on ubuntu 9.04

lspci finds it but it does not work my card is pluged in but nothing in the filemanager. It used to work with 8.10

Here's what lspci returns:
```

06:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller


```

---

### Post by libertydog on 2009-04-30
Same issue here with my HP DV4-1222nr

```
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

---

### Post by K. Hendrik on 2009-04-30
Hi i just fixed the Problem after reading this [page]("http://marc.info/?l=linux-kernel&m=122509648027303&w=2")

I just createt a new file called "cardreader-fix.conf" in "/etc/modprobe.d/"
with just the line "options sdhci debug_quirks=1" and now everything works

---

### Post by jeferod83 on 2011-01-11
Tks Hendrik... this tip fixed the problem on my DV4 2112BR.

---

