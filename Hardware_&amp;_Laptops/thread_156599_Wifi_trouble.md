---
title: "Wifi trouble"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by GatorV on 2006-04-07
Hi All, I installed Breezy in my Laptop, it has a SMC2635W PCMIA Card, the problem is that when I install gtkwifi it says my card doesn't support scanning :confused:, I know it does work under Windows, so can anyone help me?

My card is detected as RT2400PCI with iwconfig... 

Thanks in Advance!

---

### Post by lnxpwr on 2006-04-07
let's say your card is recognized as "eth1" than give this a try:
sudo iwconfig eth1 mode monitor

---

### Post by GatorV on 2006-04-07
mmm nope, that doesn't do anything, it still says it doesn't support scanning...

---

### Post by lnxpwr on 2006-04-09
which application you are using for scanning ?

---

### Post by GatorV on 2006-04-09
I tried, from terminal, and from gtkwifi, and both say my card don't support scanning, I am thinking that I need a new driver for my card but I don't know how to install it or if it exists...

---

### Post by GatorV on 2006-04-10
Well managed to find a fix :D

[http://www.ubuntuforums.org/showthread.php?t=76804](http://www.ubuntuforums.org/showthread.php?t=76804)

used that guide but with my card drivers (had to extract the exe, then the MSI), and now everything works with ndiswrapper. :D

BTW, does somebody now if I can delete the driverswlan dir I made to extract the inf?

---

### Post by mahfiaz on 2006-05-12
As ndiswrapper is supposed to make a copy of all files needed to its own folder, this has to be safe.

---

