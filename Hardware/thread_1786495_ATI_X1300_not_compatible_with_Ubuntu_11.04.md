---
title: "ATI X1300 not compatible with Ubuntu 11.04?"
date: 2011-06-19
forum: Hardware
---

### Post by bricolux1 on 2011-06-19
I'm trying to install mythbuntu on a "not so new PC" which has a ATI X1300 graphic card. Installation went fine except for the grafic card driver. I wanted to install the one from AMD as everybody recommends it. 
Problem it does not install and says it is not compatible with the current 11.04 ubuntu version??? Is it true ?? that card is not so old.
If not true, can anyone tell me where and how to install a driver for that card?
many thanks,
NB. I'm a neebee in linux, so...

---

### Post by ajgreeny on 2011-06-19
ATI do not make a linux driver for that card any more and the open source driver is not good enough for unity to run.  It's a well documented problem, without a complete solution, but if you want to at least see more or less what unity is, and what it can do, install unity-2d from synaptic or software centre, logout and then at the session menu choose unity-2d.

---

### Post by Yellow Pasque on 2011-06-20
You messed up your install. Run these commands to reset it: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

See this for detail as to why the proprietary driver doesn't work: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

