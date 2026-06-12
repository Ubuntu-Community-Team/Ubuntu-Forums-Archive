---
title: "System Requirements"
date: 2010-08-08
forum: Hardware
---

### Post by ChuckyZ28 on 2010-08-08
I am in the process of converting all of the computers that I own to ubuntu and I am trying to find information on the system requirements so I can upgrade to the latest verson that will run sable on my system. I have tried 10.4 and it most certainly is not working as I do not have enough RAM to support the OS. Does anyone know where I can get this information? And where the older versions are?

System Specs: IBM Thinkpad R51e
Processor:Intel Celeron 1.60ghz
RAM 704 MB

---

### Post by cpmman on 2010-08-08
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by ChuckyZ28 on 2010-08-08
It states there that the min system requirements is 256mb ram, if that is the case why does it run so slowly when I boot from USB Flash Drive?

As an aside I looked on Wikipedia and it states 1 gig of ram is required, someone should let them know.

---

### Post by cascade9 on 2010-08-08
Wikipedia would be going off this- 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

For normal ubuntu, the recommended**** minimum system requirements is 1GB. For Xubuntu its 256MB (IMO, thats not enough, xubuntu isnt that much lighter than ubuntu). Lubuntu should run pretty well on 256MB. 

As for why your system is running slow from a USB flash drive, even if its on a USB 2.0 port, its still going to run at about 1/3 of the speed of any modern HDD, and about 1/2 the speed of older HDDs. If its on a USB 1.0/1.1 port, thats going to make things a lot worse. 

The ATI X200M video wouldnt be helping matters either.....

---

### Post by ubu_lin on 2010-08-08
Your system is enough to run Ubuntu 10.04, I m running it on 512 Ram and have no problems, To get speed just u need to install on HDD instead of trying from USB flash drive.

---

### Post by PresenceofMind on 2010-08-08
> **ChuckyZ28 said:**
> It states there that the min system requirements is 256mb ram, if that is the case why does it run so slowly when I boot from USB Flash Drive?

As an aside I looked on Wikipedia and it states 1 gig of ram is required, someone should let them know.

PATA/SATA (PATA is old tech and SATA is the new tech) have larger bus width and higher bandwidths than USB.... so USB carries a lot less data per second than PATA or SATA (used by internal hard drives/optical drives) and hence, things will run slower.

---

