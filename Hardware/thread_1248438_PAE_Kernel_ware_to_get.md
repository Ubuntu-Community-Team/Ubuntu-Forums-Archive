---
title: "PAE Kernel? ware to get"
date: 2009-08-24
forum: Hardware
---

### Post by Ravernomina on 2009-08-24
As the titel says im looking for a PAE Linux kernel so i can have my 4 gigs of RAM and not go back to Mac OS X to get it... Any sudgestions?! Thanks

Ravernomina

---

### Post by celthunder on 2009-08-24
Just use 64 bit which supports 4gb to begin with and install the 32 bit libraries if you need them.

---

### Post by Ravernomina on 2009-08-24
i hate 64 bit ubuntu... Makes alot unstable

---

### Post by PatrickVogeli on 2009-08-24
> **Ravernomina said:**
> i hate 64 bit ubuntu... Makes alot unstable
wow... nice comment

---

### Post by cherva on 2009-08-24
Open a terminal and execute:
```
 sudo apt-get install linux-headers-server linux-image-server linux-server
``` then just reboot and you are done.

---

### Post by cherva on 2009-08-29
Please mark this thread as solved if the above command worked for you so when other people they can see its solved.

---

### Post by chrisfu on 2009-09-02
Am I correct in assuming that this kernel doesn't lack anything that the standard "generic" kernel has, and merely has several additions in order to support various server CPU/memory configurations?

---

