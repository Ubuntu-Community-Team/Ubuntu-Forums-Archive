---
title: "HP pavilion problems"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by mixed_mojo on 2007-01-04
I have an HP pavilion 9000 series and cannot install dapper or edgy on it.  They install just fine on my pavilion 1000 series.  It boots from either an image CD or the DVD, but does not finish and will go dormant causing me to force a shut down to return to windows.  My Dynebolic distro works with almost no problems, just not ubuntu.  I was wondering if anyone has heard of the same problem with newer laptops.

---

### Post by wlandsch on 2007-01-05
Tried 
ide=nodma
as boot option?

---

### Post by jcaveman on 2007-01-05
The HP Pavilion 9000 series is almost virtually identical the Pavilion dv6000 and the Compaq Presario V6000 series.  See the other posts on here concering set up of those machines.

I had luck by using the following kernel parameters on boot:

noapic irqpoll noirqdebug

---

