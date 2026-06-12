---
title: "[display] Aspire 3810T NOK"
date: 2011-08-01
forum: Hardware
---

### Post by littlebigman on 2011-08-01
Hello

I successfuly installed Ubuntu 11.04 through the NetInstall option on an [Aspire 3810T]("http://www.pcworld.com/product/61705/acer_timeline_3810t.html?p=specs") laptop.

Using the default option, the laptop boots OK, I can ssh to it OK, but the screen on the host just displays a blinking cursor. I assume the stock Ubuntu doesn't have the right display driver:

```

root@ubuntu:~# lshw -short
H/W path               Device     Class       Description
=========================================================
/0/100/2                          display     Mobile 4 Series Chipset Integrated Graphics Controller

```

Has someone seen this, and knows what to do?

Thank you.

---

