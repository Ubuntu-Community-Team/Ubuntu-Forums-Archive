---
title: "Acer Aspire 5553g - No network at all"
date: 2010-09-20
forum: Hardware
---

### Post by phil766 on 2010-09-20
Hi, I recently bought an Acer 5553g

Here are the hardware specification : [http://www.bestbuy.ca/en-CA/product/acer-acer-aspire-15-6-laptop-featuring-amd-phenom-ii-triple-core-mobile-n830-as5553g-5855-black-as5553g-5855/10146910.aspx?path=596f3deaa15412cd191f724eb43be46fen02&lid=fp-10146910-aceraceraspire156laptopfeaturi-en]("http://www.bestbuy.ca/en-CA/product/acer-acer-aspire-15-6-laptop-featuring-amd-phenom-ii-triple-core-mobile-n830-as5553g-5855-black-as5553g-5855/10146910.aspx?path=596f3deaa15412cd191f724eb43be46fen02&lid=fp-10146910-aceraceraspire156laptopfeaturi-en")

I'v try bot 64bit and 32bit version of ubuntu 10.04, but no success, I'm getting  nothing from my wireless adapter and my ethernet port. What can I do ?

---

### Post by phil766 on 2010-09-21
No one can help me plz ?
I realy need ubuntu and I don't want to virtualize it.

---

### Post by phil766 on 2010-09-22
Cmon guys, this is a serious thread

:(

---

### Post by bimbofred on 2010-09-24
I had the same problem and found that if you remove gnome's network manager by typing:
```
sudo apt-get remove network-manager
```
and:
```
sudo apt-get remove network-manager-gnome
```
Then install wicd in software centre you should be fine.

---

