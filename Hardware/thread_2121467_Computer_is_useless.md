---
title: "Computer is useless"
date: 2013-03-02
forum: Hardware
---

### Post by mr plow on 2013-03-02
hi,

i have done a fresh install of ubuntu 12.04 LTS and then i decided to get the most out of my hardware and install the ATI drivers for my Gigabyte HD 6670 2GB graphics card. because i am running a 64 bit CPU and running Dual channel memory i though it would be best to install a 64 bit OS. now my problem is after installing the ATI drivers from the additional hardware drivers section in ubuntu once i rebooted i have nothing but a BLACK screen i have tried EVERY FIX from the Xorg wiki (relevant to this problem). i am out of ideas i have edited xorg.conf and i have been through the log file too many times to count. guys this will be the last time i ask about this problem after that Ubuntu will be deleted.

error is xorg server fatal error no screens found (i have tried all the fixes that xorg has posted in there wiki)

i can not get into failsafe X

i can only get a root shell.

i get a black screen only when trying X

thanks.

---

### Post by QIII on 2013-03-02
Did you install fglrx or fglrx-updates?  The latter is generally problematic.

Before you rebooted, did you do 

```
sudo amdconfig --initial
```?

---

### Post by mr plow on 2013-03-02
> **QIII said:**
> Did you install fglrx or fglrx-updates?  The latter is generally problematic.

Before you rebooted, did you do 

```
sudo amdconfig --initial
```?

no i just installed from the ubuntu hardware additional drivers in system settings.

and after a bit of research i found out i had to do the --initial so i did that from the root shell after the big fizzle.

thanks,

as this is a fresh install (and 12hrs of HDD partitioning) im going to redo the lot hope all goes well.

---

