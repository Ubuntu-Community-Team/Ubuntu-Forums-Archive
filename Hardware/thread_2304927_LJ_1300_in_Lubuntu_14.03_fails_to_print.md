---
title: "LJ 1300 in Lubuntu 14.03 fails to print"
date: 2015-12-01
forum: Hardware
---

### Post by jan53 on 2015-12-01
I have an old HP LJ 1300 connected to desktop via USB, system is Lubuntu 14.03 LTS.
The test page and/or printing documents in Libre office Writer is OK while printing PDF documents from Evince viewer or from directly from Firefox dose not work, the printer only blinks and the no output.
Any remedy ?

---

### Post by jan53 on 2015-12-01
I also opened the error log in /var/log/cups/error-log   and it says: 
E [01/Dec/2015:18:30:49 +0100] [Job 85] Unable to queue job for destination "hp_LaserJet_1300".
The printer meanwhile blinks like in printing and then after a long while it stops blinking like when finishes printing.
But no print ouptut appears.

---

### Post by jan53 on 2015-12-02
I already solved the problem (based on advice given to me in local Czech Ubuntu forum). It was simple - by selecting a different device driver from the list of HP 1300 drivers in Linux. Instead of using recommended driver I select HPLaserjet 1300 pcl13 hpcups 3.15.11 driver and all printing is perfect now.

---

