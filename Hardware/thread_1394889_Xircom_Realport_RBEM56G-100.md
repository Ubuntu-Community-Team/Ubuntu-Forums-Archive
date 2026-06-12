---
title: "Xircom Realport RBEM56G-100"
date: 2010-01-31
forum: Hardware
---

### Post by flygin on 2010-01-31
The card is recognized (lspci) and the ethernet works out of the box. A module xircom is loaded. But I could not make the modem work.

I don't know what serial port (stty?) the modem is on, how to find the serial port and if I have to load another module.

pppconfig did not find the modem. I tried with stty0 to 4, pon did do something, but the processes died after. ifconfig -a did not show any connection and the ppp-errors were empty.

---

