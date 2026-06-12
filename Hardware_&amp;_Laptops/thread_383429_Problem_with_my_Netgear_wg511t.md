---
title: "Problem with my Netgear wg511t"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Ryan_B on 2007-03-13
I was suprised when i first installed 6.06 that my wg511t adapter worked without any installation of drivers. Now i have upgraded to 6.10 and for some reason now the adapter does not work anymore. Im a n00b at linux so can anyone shed any light on how i may get it working again?

Thanks in advance.

:confused:

---

### Post by Ryan_B on 2007-03-14
*bump*

Is it worth installing some drivers for it? I attaempted to use Wine to install the CD i got with it but it didnt work. Can anyone point me in the direction of a driver for it?

:(

---

### Post by Azilla on 2007-03-14
Could you type the command below in your terminal, this is to figure out what chipset your card uses. Once you've logged in and it's displayed the info just copy/paste it here.
;)

--
# sudo lspci | grep Ethernet

---

### Post by Shadoweater12081980 on 2007-03-14
You could try ndiswrapper using the windows driver.

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by supermarchino on 2007-03-15
> **Shadoweater12081980 said:**
> You could try ndiswrapper using the windows driver.

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

No. WG511T has native support. Just install restricted modules for your kernel, your device will be /dev/ath0.

Ciao

---

