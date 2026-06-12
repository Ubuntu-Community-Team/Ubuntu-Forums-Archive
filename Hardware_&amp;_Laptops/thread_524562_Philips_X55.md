---
title: "Philips X55"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by crystalgeek on 2007-08-13
Hi All,

I have been trying to install Ubuntu 7.04 onto my Philips X55 for the last few days and finally found this post. [http://ubuntuforums.org/showpost.php?p=1844744&postcount=18](http://ubuntuforums.org/showpost.php?p=1844744&postcount=18)

Being a totall n00b what is this line /lib/modules/(kernel)/drivers/net 
 as there is no dir command i get stuck after cd'ing to modules as I don't know what kernel im using. I downloaded the most upto date Alternative CD from the kent mirror (UK - GB) 

Any help would be greatly appreciated

---

### Post by crystalgeek on 2007-08-14
So I figured it out finally found the information i needed. 

/2.6.20-15-generic/kernel/drivers

:)

---

### Post by Discombobulated on 2008-02-09
Potential solution:  > [This laptop] has problems with Linux. The most Linux-Distributions crash at the hardware detection.
At my tests with Ubuntu 7.04 Feisty Fawn, I have found two kernel modules that cause a crash:

    * 8139too: Realtec 8139C Ethernet Driver (MMIO)
    * sdhci: Treiber [driver] for SD/MMC Cardreader 

Because Ubuntu has no parameters to prevent the load of kernel modules, I have build a modified installation CD. It doesn't contain the SDHCI module and a 8139too module compiled for PIO only access.

The informations for Ubuntu 7.04 are still here but i will disable the torrent next time.

Ubuntu 7.10 Gutsy Gibbon: New Version new game. The crashing problems are the same. Display resolution is correct now out of the box but there are new problems with the sound mixer.



[COLOR="Blue"][http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)[/COLOR]

Appears to cover:

    * Averatec 2460
    * Everex Stepnote SA2050
    * Everex Stepnote SA2050T
    * Everex StepNote SA2052T
    * Everex StepNote SA2053T
    * Philips Freevents x52
    * Philips Freevents x53
    * Philips Freevents x54
    * Philips Freevents x55
    * Philips Freevents x56
    * Philips Freevents x59
    * Twinhead Stylebook H12Y

I'm downloading it now - torrent appears dead ATM, will seed for as long as possible as soon as it's down.  Suggest anyone needing it hits the torrent first to save this very helpful chaps bandwidth!

---

### Post by derjames on 2008-02-14
One of the bugs is reported here...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90271](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90271)

---

