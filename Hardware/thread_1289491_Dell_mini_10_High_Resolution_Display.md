---
title: "Dell mini 10 High Resolution Display"
date: 2009-10-12
forum: Hardware
---

### Post by TCSnyder on 2009-10-12
i have a dell mini 10 and ubuntu does not detect the display. when i go into
System=>preferences=>Display 
is says the display is unknown.

now it has 1024x768 resolution but it is made for 1366x768. 
i have tried evrything in [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") but  nothing worked for me. 

Any suggestions??

here are the display specs??

this is the name if it helps
intel graphics media accelerator 500

---

### Post by undfined on 2009-12-01
Mini 10 or 10v?

On my 10 
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```from: 
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) did the trick.

I don't know about the 10v.

I should have researched a little more before I bought mine.  It looks great now, but that was a pain to find.

---

