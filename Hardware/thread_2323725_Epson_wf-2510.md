---
title: "Epson wf-2510"
date: 2016-05-07
forum: Hardware
---

### Post by 0N3 on 2016-05-07
This printer worked fine in 14.04 with no problems but just can't seem to get it to work under Ubuntu 16.04. It shows up under network printer and when I go to set it up it says something about searching for drivers it then proceeds to install the driver..... it then takes me to a screen to something about generic printer I follow the instructions but it never prints anything.

[ATTACH=CONFIG]268895[/ATTACH]

---

### Post by 0N3 on 2016-05-07
Solved it with:

```
sudo apt-get install printer-driver-escpr


```

It wasn't accepting the epson-inkjet-printer-escpr_1.6.5-1lsb3.2_amd64.deb from the epson website.

---

### Post by pauli-pilvi-wippies on 2016-05-16
Thank you! I just upgraded to 16.04 and had the same problem.

---

### Post by Linuxisfast on 2016-05-16
It was truly an oversight of Canonical to follow suit of Debian and remove LSB. Not only Epson but Canon and Brother printers and some others need it for driver install. Only HP works with HPLIP but then that means if one has to use Ubuntu, its HP printer and rest out unless Epson models get supported by escpr. However there are ink status utilities and nozzle cleaning utilities that too depend on LSB to be installed on system. Please bring back LSB.

---

