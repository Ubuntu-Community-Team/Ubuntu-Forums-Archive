---
title: "HDD seems to be broken"
date: 2010-04-27
forum: Hardware
---

### Post by obsrv on 2010-04-27
Hello,
I have Western Digital 320GB HDD and it seems that it's broken. System is very slow and when I type in a terminal as root:

```
root@pirate:~# hdparm -d /dev/sda5

/dev/sda5:
 HDIO_GET_DMA failed: Inappropriate ioctl for device
root@pirate:~# 

```

A few days ago on the same HDD was installed Windows 7, and it was unable to boot. I remember using some kind of SMART tool to check HDD health, maybe you know the name of that app? Or maybe there is not CLI, but GUI version of a program that can check status of HDD using SMART?

Thank you.

BTW, I enjoy Lucid Lynx RC a lot!

---

### Post by antenna on 2010-04-27
palimpset (available from System->Administration->Disk Utility) should be able to give you SMART data

---

### Post by obsrv on 2010-04-27
When I launch self test I get "FAILED (READ)", where I can find verbose information?

---

### Post by antenna on 2010-04-27
I'm not sure to be honest, that's not particularly helpful of it if it doesn't offer you more information than that.

Your best bet may be to just install smartmontools and try that, not gui though I'm afraid.

---

### Post by obsrv on 2010-04-27
I have installed the package but I cant find the binary of smartmontool. Maybe you could write me a command line how to run it on /dev/sda and get verbose info?

---

### Post by psusi on 2010-04-27
The binary is smartctl.  Try sudo smartctl -A /dev/sdb.

---

