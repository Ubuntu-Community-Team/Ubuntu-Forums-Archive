---
title: "Intel Onboard graphics card"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by Iyatos on 2006-11-27
I can't find any drivers for my 82915G/GV/910GL express chipset graphics card, for ubuntu can anyone help me, i am trying to run a program but it does not detect the card at all and it is working correctly. Otherwise the card runs fine.

---

### Post by taurus on 2006-11-27
Use the 915resolution driver for it then!  Make sure you enable both universe & multiverse by removing the # in front of lines with those two words in /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install 915resolution
```
Or use synaptic to install it...

---

