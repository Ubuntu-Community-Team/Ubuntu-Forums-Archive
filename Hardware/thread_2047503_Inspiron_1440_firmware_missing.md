---
title: "Inspiron 1440 firmware missing"
date: 2012-08-25
forum: Hardware
---

### Post by Virinder on 2012-08-25
I recently intalled ubuntu 10.10 desktop edition and when i try to use my wi-fi , i ws unable to use it,as it shows firmware missing.As i am new to ubuntu dont know what to do,,...Please help...!!!

---

### Post by ahallubuntu on 2012-08-25
Ubuntu 10.10 is no longer supported.  You would be better off with several other versions of Ubuntu.  Ubuntu 12.04 LTS is more likely to support your wireless card automatically.  If you don't want to use that version for some reason, try 11.04 - which is still supported though only for a few more months.

If you still can't get another version of Ubuntu to support your wireless card, post more information about the card.  Dell ships several different models of wireless cards with most of their laptops.  In a terminal type:

```
sudo lshw -c network
```

and post the results for the one that says "description: Wireless Interface"

---

