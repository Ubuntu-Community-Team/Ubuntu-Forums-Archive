---
title: "Does hdparm work on SATA and eSATA drives?"
date: 2008-10-27
forum: General Help
---

### Post by the8thstar on 2008-10-27
Does hdparm work on SATA and eSATA drives? I've seen in /etc/hdparm.conf that a lot of instructions seem to refer to IDE drives, hence my question since my laptop has a SATA drive and I also have an eSATA external hard drive.

Thanks for your help!

---

### Post by techstop on 2008-10-27
```
man hdparm
```

> NAME
       hdparm - get/set SATA/ATA device parameters

SYNOPSIS
       hdparm [ flags ] [device] ..

DESCRIPTION
       hdparm  provides  a command line interface to various kernel interfaces supported by the Linux SATA/PATA/SAS "libata" subsystem and  the  older IDE  driver  subsystem.   Some options may work correctly only with the latest kernels.


Looks like it for sata at least. Not sure about esata.

---

