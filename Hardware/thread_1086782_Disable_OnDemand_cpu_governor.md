---
title: "Disable OnDemand cpu governor"
date: 2009-03-04
forum: Hardware
---

### Post by Jordanwb on 2009-03-04
Yesterday I got an Acer aspire 5515 and I got rid of Vista and put Ubuntu on it. Whenever my laptop starts up the Performance applet defaults to ondemand. How do I get it to default to Performace?

I've blacklisted the cpufreq-ondemand module but the above still happens.

[Edit]

Also the network manager doesn't save my network configurations.

---

### Post by Jordanwb on 2009-03-20
Bump.

---

### Post by darthfruitloop on 2010-01-01
[http://blog.mpathirage.com/2009/10/04/how-to-disable-dynamic-frequency-scalingcpu-throttling-in-ubuntu-jaunty9-04/](http://blog.mpathirage.com/2009/10/04/how-to-disable-dynamic-frequency-scalingcpu-throttling-in-ubuntu-jaunty9-04/)

did the trick for me :)

---

### Post by Jordanwb on 2010-01-01
I had forgotten about this thread, since I had posted it in march. Since then I found out about "update-rc.d" and had disabled the ondemand init script with that.

---

