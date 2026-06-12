---
title: "HP SimpleSave 320GB HD problem"
date: 2009-11-07
forum: Hardware
---

### Post by c_winwood on 2009-11-07
I am currenty running Ubuntu 8.10 and have just brought the HP SimpleSave 320Gb Hard Disk.  Ubuntu fails to recognise it.  Anybody come across a similar problem, or is anyone running it sucessfully on 8.10, 9.04 or 9.10?  Any help would be appreciated.

---

### Post by GJCGJC on 2009-11-22
This is running out of the box on 9.10 for me on a Dell Inspiron laptop. Only problem I'm having now is trying to rename it to get rid of the space between HP and SimpleSave.

---

### Post by Bremm on 2010-03-03
> **GJCGJC said:**
> This is running out of the box on 9.10 for me on a Dell Inspiron laptop. Only problem I'm having now is trying to rename it to get rid of the space between HP and SimpleSave.

Try "sudo dosfslabel /dev/$UNIT HPSimpleSave" (without quotes), where $UNIT is your disk partition (in my case, sdb1).

---

