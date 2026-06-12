---
title: "ATI Radeon Xpress 200M driver install"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by swaybox on 2008-01-26
Hi, Im very new to ubuntu. I have a ATI Radeon Xpress 200M card in my Pavilion ze2000 and I was just wondering if anyone knew how to install the drivers for the ATI Radeon Xpress 200M video card. If anyone could help I wouild greatly appreciate it.

---

### Post by geekphreak on 2008-01-26
> **swaybox said:**
> Hi, Im very new to ubuntu. I have a ATI Radeon Xpress 200M card in my Pavilion ze2000 and I was just wondering if anyone knew how to install the drivers for the ATI Radeon Xpress 200M video card. If anyone could help I wouild greatly appreciate it.
 
Simply follow [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)
Worked like a charm for me. Compiz Fusion runs smoothly.

---

### Post by meindian523 on 2008-01-26
Actually,System>>Administration>>Restricted Drivers Manager.
Check the box for ATi Accelerated Graphics Driver.Let Ubuntu handle the rest.And,yes,Compiz Fusion runs smoothly here too.

---

### Post by erfahren on 2008-01-26
> **meindian523 said:**
> Actually,System>>Administration>>Restricted Drivers Manager.
Check the box for ATi Accelerated Graphics Driver.Let Ubuntu handle the rest.And,yes,Compiz Fusion runs smoothly here too.
with that driver you need to install xserver-xgl to run visual effects with an ATI card

---

### Post by meindian523 on 2008-01-26
That's true,but we have to wait till fglrx actually supports AIGLX to skip that step unless you are willing to "test" new drivers from the ATi stable.AFAIK,that's not the case yet.

---

