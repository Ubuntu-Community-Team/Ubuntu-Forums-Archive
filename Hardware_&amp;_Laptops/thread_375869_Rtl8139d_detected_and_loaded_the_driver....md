---
title: "Rtl8139d detected and loaded the driver..."
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by sriram on 2007-03-04
hi guys i am breaking my head on installing the network card as eth0
my network card driver is loaded as 8139too.ko and lspci shows my card as ethernet controller,modprobe the driver file also works ..
my prob here is tat the card is not detected as eth0 in network-admin ...
i use a pppoe connection to connect to the net , it works fine in winxp using raspppoe...
i have pppconf but its unable to detect the card....
if i run ipconfig it shows me only lo interface not the card no eth0 ..

output of lsmod
Module Size Used by
8139too 30017 0
mii 5441 1 8139too

if i ran the command to grep for "eth" and nothing was returned 

i have tried everything possible by me ..

---

### Post by newagelink on 2007-03-04
I wish I could help, but I have trouble getting my own connection in Ubuntu (wireless). Hope it works out for you ...

---

