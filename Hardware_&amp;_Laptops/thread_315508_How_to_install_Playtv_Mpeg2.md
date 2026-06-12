---
title: "How to install Playtv Mpeg2"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by Mainframe on 2006-12-09
I dont now how to install this playtv mpeg2.

---

### Post by psavva on 2007-05-18
I got the same, card. 

What do you need help with?

You need to install the BTTV Drivers 
modprobe bttv

it should detect your card automatically,. 

You card is probably type 139 or type 72

to get this to work, all you need to do is 
```

sudo modprobe bttv card=139

```
then once that's done. You'll need to install TVTIME 
i suggest doing that from the Synaptic Package Manager

---

