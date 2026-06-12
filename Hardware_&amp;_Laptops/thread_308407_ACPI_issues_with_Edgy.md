---
title: "ACPI issues with Edgy"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by dbouwer on 2006-11-28
Running 6.10 currently.... Compaq Evo N620c laptop

I found that there is a problem with the acpi support in this version.

I get short freezes when it throttles the cpu. When I bypass the throttling and set the speed, it works without any problems. I don't have this problem in dapper or suse or knoppix.

Is it maybe the kernel version? 2.6.17-10-generic? 

Also, when I boot from hibernation, the kacpid and kacpi_notify instances goes crazy!

These issues are only on Edgy!

---

### Post by rakr on 2006-11-30
Appears as though there is a configuration error that has been reported in the past but has slipped through on Edgy.  This worked for me.. 

[http://ubuntuforums.org/archive/index.php/t-75598.html](http://ubuntuforums.org/archive/index.php/t-75598.html)

---

### Post by dbouwer on 2006-12-01
Is much better, but still stops audio/mouse/display/system for short millisecond bursts...

Changing the governor to performance sorts it out.....

Painfull because it works 100% on dapper....

---

### Post by dbouwer on 2007-01-09
Throttling to 100% cpu doesn't sort it completely......

Is there anything else I can try? This problem is only in Edgy! Dapper was perfect...


The whole system freezes for milliseconds, often, and is very anoying!!

---

### Post by dbouwer on 2007-01-10
Finally found a cure!!!

kacpid and kacpi_notify is set to -5 priority, changed the priority to normal, and now all is perfect!!!


Any idea how I can start that process with a lower priority when booting?

---

### Post by amgat on 2007-03-01
I have the same problem with my Evo N620c. Set the priority to normal on the mentioned processes, and the "lag" is gone. How can we make this change permanent?

---

### Post by blierp on 2007-03-02
this problem has been driving me crazy since i installed edgy, thanks for finally providing a solution!

---

