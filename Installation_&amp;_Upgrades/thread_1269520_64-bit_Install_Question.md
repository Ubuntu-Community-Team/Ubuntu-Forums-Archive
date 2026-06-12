---
title: "64-bit Install Question"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by wrwarwick on 2009-09-18
Quick question....

Yesterday I moved my /home directory to a separate partition on my Ubuntu 32-bit laptop. If I begin the install with 64-bit, will all of my settings be saved? Or is the install too different?

---

### Post by oldos2er on 2009-09-18
Yes, your settings will be saved. During installation when the partitioner runs, you'll need to specify the same /home partition you have now as /home; make sure you do not set it to be formatted--I think there is a box you need to uncheck to accomplish that.

---

### Post by wrwarwick on 2009-09-18
Ok that is reassuring. 

Will it keep my hardware config; ie, fglrx, wireless drivers, sound config, compiz settings etc? And all the applications will work correctly?

---

### Post by oldos2er on 2009-09-18
> **wrwarwick said:**
>  Will it keep my hardware config; ie, fglrx, wireless drivers, sound config, compiz settings etc? 

 No, it will install 64-bit versions of everything. Your compiz settings will work after you enable the restricted drivers.

---

