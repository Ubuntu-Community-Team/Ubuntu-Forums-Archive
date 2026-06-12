---
title: "Hardware RAID controller for Ubuntu"
date: 2008-08-31
forum: Hardware
---

### Post by ubumac on 2008-08-31
I am looking for a SATA raid card that is supported by Ubuntu. I have found several 'Linux Compatible' cards, but have found various postings indicating that folks have encountered issues when trying to implement those cards with Ubuntu. For example, the Promise TX2300 is Linux compatible, but specifically does not mention Ubuntu as being supported.

Any help is appreciated.

---

### Post by srpenney on 2008-10-12
I can tell you for certain that the Promise FastTrak 2300 PCI raid controller does work with Ubuntu as a softraid array, just not right out of the box so to speak.  I have a raid1 array working with two 500GB drives and hardy heron but it was not supported by the base install.  

The forum thread [http://ubuntuforums.org/showthread.php?t=945991&highlight=tx2300](http://ubuntuforums.org/showthread.php?t=945991&highlight=tx2300) will tell you how to get it up and running with the Promise TX2300

Cheers,

---

