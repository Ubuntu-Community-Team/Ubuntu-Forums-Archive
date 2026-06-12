---
title: "Ubuntu Natty Printing"
date: 2011-05-18
forum: Hardware
---

### Post by Jimstehrman on 2011-05-18
Hey all,

I have recently been having issues printing from Ubuntu. I have an HP LaserJet P1005, which worked wonderfully with Ubuntu in the past. One day I was printing a long document, and ran out of paper. Now it will simply not print anything which is placed in the que. The job will disappear after about 30 seconds. The printer itself still works fine, I can print from Vista with no issues.
Any thoughts?

Thanks!

---

### Post by Barba14 on 2011-05-18
> **Jimstehrman said:**
> Hey all,

I have recently been having issues printing from Ubuntu. I have an HP LaserJet P1005, which worked wonderfully with Ubuntu in the past. One day I was printing a long document, and ran out of paper. Now it will simply not print anything which is placed in the que. The job will disappear after about 30 seconds. The printer itself still works fine, I can print from Vista with no issues.
Any thoughts?

Thanks!

I had a similar problem and solved following instructions posted here: [http://askubuntu.com/questions/38198/hp-laserjet-p1005-stopped-working-after-upgrade](http://askubuntu.com/questions/38198/hp-laserjet-p1005-stopped-working-after-upgrade)

---

### Post by collisionystm on 2011-05-18
> **Jimstehrman said:**
> Hey all,

I have recently been having issues printing from Ubuntu. I have an HP LaserJet P1005, which worked wonderfully with Ubuntu in the past. One day I was printing a long document, and ran out of paper. Now it will simply not print anything which is placed in the que. The job will disappear after about 30 seconds. The printer itself still works fine, I can print from Vista with no issues.
Any thoughts?

Thanks!


Install HPLIP from the software center. You should be using it anyways. Its the best thing for HP printers

---

### Post by Jimstehrman on 2011-05-19
Hey,

No luck, same thing happens, even though it appears HPLIP has successfully identified and set up my printer, it recognizes it, and even tell me how much toner I have, but will not print. I tried manually setting up my printer, but it tells me that the driver installation fails.

---

### Post by collisionystm on 2011-05-20
> **Jimstehrman said:**
> Hey,

No luck, same thing happens, even though it appears HPLIP has successfully identified and set up my printer, it recognizes it, and even tell me how much toner I have, but will not print. I tried manually setting up my printer, but it tells me that the driver installation fails.

Did it let you install the required HP plugin?

You can manually get the plugin from here


```
wget http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run
```

Then 

```
sudo sh hplip-3.11.1-plugin.run
```

This will install the required HP proprietary Plugin.

---

