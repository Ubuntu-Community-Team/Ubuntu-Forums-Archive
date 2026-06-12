---
title: "Acer Laptop not recognizing wireless"
date: 2009-12-23
forum: Hardware
---

### Post by jake99 on 2009-12-23
Hi, i got an acer laptop model: Travelmate 7520 a year ago and it had windows xp on it. Just last night i decided to try to switch over to ubuntu 9.10.

Everything worked good it seemed but when i opened up firefox it shows that i am not connected to internet, and my wireless internet light on the bottum of my computer is not turned on....

I am brand new to linux, any help would be awsome! :) thx!

---

### Post by roger_1960 on 2009-12-23
Hi

Sorry if you have already tried this,but at top right of the screen, right click on the networking icon and check the boxes for "enable networking" and " enable wireless"

---

### Post by coffeecat on 2009-12-23
Let's see what wireless device you've got. Open a terminal (Applications > Accessories > terminal) and post the output of:

```
lspci | grep Wireless
```If you don't get any output from that, try:

```
lspci | grep 802.11
```

---

