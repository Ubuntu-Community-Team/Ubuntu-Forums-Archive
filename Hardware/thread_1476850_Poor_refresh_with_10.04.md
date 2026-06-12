---
title: "Poor refresh with 10.04"
date: 2010-05-08
forum: Hardware
---

### Post by jataomm on 2010-05-08
I just upgraded from Karmic to 10.04 and it's rendered my laptop virtually unusable.  Refresh rate appears to have fallen to about 3 seconds!  (just finding this forum and getting to it was an excruciating task!)

I am running on a Toshiba Equium L20-197 which was fine on the previous version.  It was a 2G Ram upgrade.

Any suggestions?

---

### Post by dino99 on 2010-05-08
maybe a graphic card driver issue: look at hardware driver (system admin) if yours is activated.

what is your graphic card ?

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by jataomm on 2010-05-08
Apparently my graphics processor is : ATI RADEON XPRESS 200M IGP

---

### Post by jataomm on 2010-05-08
Getting the very latest update appears to have fixed the problem.  It seems the advice is here to be found after all, but with that slow refresh rate just getting to this forum was a wild pain!

---

