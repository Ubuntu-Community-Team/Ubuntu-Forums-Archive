---
title: "pcmcia questions"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by BigCdaAnswer3 on 2007-02-09
hello all, i have a hp zv5000 laptop with the following output of lspcmcia:

ccole@forest:~$ lspcmcia  -v
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.0)
        Configuration:  state: on       ready: unknown
                        Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:04.1)
        Configuration:  state: on       ready: unknown

I'm trying to use a sandisk compactflash pc card adapter to read/write to a 2.0 gb flash card that i just bought. This is the first time i've tried to use a pcmcia card and i have no idea how to access it. I've stumbled across pccardctl but it seems relatively unuseful at this point. Can anyone point me in the right direction???? I'm running feisty w/ daily updates if that helps.

---

### Post by marhp on 2007-02-18
Hi I have an ibm t42 with same issue on herd 4 have not been able to find any help. I am off to launchpad to see if a bug has been filed.

---

