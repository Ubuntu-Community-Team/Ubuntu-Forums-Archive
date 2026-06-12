---
title: "Disable ALL Drives on Live CD"
date: 2009-10-22
forum: Hardware
---

### Post by johnzollo on 2009-10-22
I am trying to disable all drives when booting off the live cd.  (I am trying to install a driver for my raid card.)  I've tried all the following from the boot prompt, but none of them work:

```
hda=noprobe hdb=noprobe hdc=noprobe hdd=noprobe

sda=noprobe sdb=noprobe sdc=noprobe sdd=noprobe
```
and...
```
noprobe=ata1 noprobe=ata2 noprobe=ata3 noprobe=ata4
```

So none of these work.  Is there a way to disable the automatic use of these drives on startup using the boot prompt?

I would sincerely appreciate any advice.  :)

Thanks in advance!

Sincerely,
john

PS I can post dmesg if you need it.

---

### Post by IcarusR on 2009-10-22
As far as I know physical drives are not auto mounted when using a live CD.
Am using one on my eeepc 901 now & have searched it for evidence of internal drives being mounted. 
None are listed in /etc/mtab. If mounted they should be listed. This supports my origional thoughts.

---

### Post by johnzollo on 2009-10-22
I believe I need the drivers not the be loaded at all (for the drives).   I'm installing a Highpoint Rocket Raid 1520 and I can't have the kernel load its own drivers.  I need it to not load anything for those drives.

I think I'[m on the right track -- any suggestions?

John

---

### Post by johnzollo on 2009-10-22
Ok.   hdx=noprobe has been obsolete for some time -- since 2.6.25 -- so that would make hdx=noprobe useless for intrepid and newer.  I've been trying the new version of that command: ide_core.noprobe=x.y , but the kernel on the live cd (for karmic) tells me it's an invalid prompt command.  Any ideas?

I'M LOSING MY MIND?!?!??

john

---

### Post by johnzollo on 2009-10-22
Well, not only is hdx=noprobe obsolete in any linux kernel, ide_core.noprobe=x.y is not appropriate for Ubuntu because we use **libata** instead of **ide** (hence all the sdx's instead of hdx's).  Will keep everyone posted...


nice command:

```
modinfo -p libata
```

check it out! 

John

---

