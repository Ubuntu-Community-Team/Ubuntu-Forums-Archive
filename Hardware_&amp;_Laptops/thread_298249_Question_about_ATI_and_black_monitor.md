---
title: "Question about ATI and black monitor"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by EscCcada on 2006-11-12
I've installed Edgy Eft on a some old machine with 256RAM and ATI Radeon 9250, put radeon driver on xorg.conf and now I have such a problem: after some time monitor gets black and says that it is "Out of range". nothing helps.
what could it be and how could I fix this?

thank you

---

### Post by diegolaz on 2006-11-12
I had a similar problem with X800 ATI. Solved the problem resintalling ati drivers following the steps from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
(I used method 1)
One of the important things I think is to disable composite for ATI cards.

good luck 
Diego

---

### Post by EscCcada on 2006-11-12
about video drivers- I've tried ati, radeon and fglrx- none helped.

and also I've got following error_log:
E [12/Nov/2006:21:41:17 +0200] Creating missing directory "/var/run/cups/certs"

there was canon i250 connected through usb port- couldn't there be this?

---

