---
title: "Screen resolution problem after update to Trusty"
date: 2014-08-24
forum: Hardware
---

### Post by DaveM59 on 2014-08-24
An hour of Googling has left me confused. My laptop has MobilityRadeon 4225/4250 graphics hardware. When I udgraded to Trusty the resolution changed -- should be 1366 x 768 but it is now 1024 x 768  which is listed in ate System/Display  as "Default." No options available. Software Updater says no proprietary drivers are installed and none are available. Some online advice  says to install the fglrx driver, others say this is a bad idea.  One topic I found says AMD/ATI no longer offers a driver for this "outdated" hardware. Please advise how I can get my screen to display correctly.  -- TIA

---

### Post by ajgreeny on 2014-08-24
Your graphic card is no longer supported by fglrx in Trusty, so I'm afraid you will have to manage with the open source driver you have at the moment.

Unfortunately I do not know how you can get back to a better resolution for your monitor, so you may have to wait for other posters who hopefully will be able to help with that.

---

### Post by DaveM59 on 2014-08-24
Thanks for confirming that my 4-year-old machine is "obsolete." I must say that does not raise my opinion of AMD/ATI. 

Anybody know a work-around for this?

TIA --

---

### Post by DaveM59 on 2014-08-28
Never mind, I just reverted to 12.04 (reinstalled).

---

### Post by Mark Phelps on 2014-08-29
> **DaveM59 said:**
> Never mind, I just reverted to 12.04 (reinstalled).

Just ... don't upgrade beyond that ... including, to 12.04.2 -- because, starting with that upgrade, the X-server version was changed, making it incompatible with the latest fglrx driver available for your video chipset. So, to continue to use the fglrx drivers, you will not be able to upgrade Ubuntu beyond what you have it set at now.

---

