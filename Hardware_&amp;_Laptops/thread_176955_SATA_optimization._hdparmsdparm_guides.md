---
title: "SATA optimization. hdparm/sdparm guides ?"
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by mips on 2006-05-15
Anybody know of guides to optimise SATA drive performance via hdparm/sdparm ???

---

### Post by mips on 2006-05-17
bump

---

### Post by mrazster on 2006-05-17
Don't know if [***THIS***](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1)
could be of any help..?!

"Good Luck"

---

### Post by tckirby on 2008-04-05
i'm having performance issues with /dev/sd? drives too... any ideas?

---

### Post by stek79 on 2008-04-05
Hi,
      please try to describe your performance problem first!

Before any tuning a performance baseline is needed. With 'hdparm -t' you can test your sequential throughput, whereas with the 'seeker' tool you can asses the performance of random workloads.

The 'seeker' tool can be found here, along with a nice HD performance description:

[http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html)

---

### Post by stefangr1 on 2008-04-05
> **tckirby said:**
> i'm having performance issues with /dev/sd? drives too... any ideas?

What sort of performance issues?

---

### Post by hokah on 2008-04-07
Lets say
[http://ubuntuforums.org/showthread.php?t=747536&highlight=hdparm](http://ubuntuforums.org/showthread.php?t=747536&highlight=hdparm)

It is amazing how ubuntu can slow down my laptop after installing windows xp I was feeling like having new laptop with double speed.

---

