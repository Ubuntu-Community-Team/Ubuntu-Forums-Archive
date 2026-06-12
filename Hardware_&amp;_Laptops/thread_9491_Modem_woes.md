---
title: "Modem woes"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by ubuntu1 on 2004-12-29
Having used Ubuntu with no problems I loaded it onto a PIII Compaq machine for my father. All seemed well until I installed a modem. I now get a message during boot saying -
PCI: Address space collision on region 7 and on region 8 as a result the modem will not activate. Having Googled for information I'm no wiser. Does anyone out there have any suggestions.

---

### Post by rbran100 on 2004-12-29
I would try first to move the Modem to a different PCI slot and see if that helps out.

 :D

---

### Post by ubuntu1 on 2004-12-29
Thanks for the reply but I've tried all of the available positions and I get the same response.

---

### Post by rbran100 on 2004-12-29
wow, that really is an obscure message.  I assume you don't have another modem to try otherwise you wouldn't be dealing with this headache......

The next thing i would try if it was me would be to clean off the brass connectors that slide into the PCI slot.  (with a pencil eraser)  :-x

---

### Post by az on 2004-12-29
1- Are you sure that the modem works?

2- If your modem has jumpers, use them.  If not,

3- sudo lspci
Note the port address (memory location) and the irq of the modem.

Boot into your bios and see if there is an onboard soundcard (or other similar hardware) that is fighting for the same numbers.

Good luck!

---

