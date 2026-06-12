---
title: "Use Areca RAID card with Ubuntu 12.04 server"
date: 2013-09-28
forum: Hardware
---

### Post by geohei on 2013-09-28
Hi.

I have an Areca ARC-1220 RAID card.

I read several articles which deal with recompiling kernel adding variables in order to make the RAID volumes visible for Ubuntu.
[http://manpages.ubuntu.com/manpages/hardy/man4/arcmsr.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/arcmsr.4.html)

Is there any other way to use the RAID volumes rather than to recompile kernel?

To my surprise, I noticed that Ubuntu 12.04 Desktop properly displays the RAID volumes of that machine. Which method does it use?

Thanks,

---

### Post by geohei on 2013-10-03
Hi.

The system recognizes the Areca RAID device, but it doesn't seem to mount the volumes.
```
root@io:/dev# dmesg | grep reca
[    3.644084] Areca RAID Controller4: F/W V1.49 2010-12-02 & Model ARC-1220
[    3.660092] scsi4 : Areca SATA Host Adapter RAID Controller( RAID6 capable)
[    3.661567] scsi 4:0:0:0: Direct-Access     Areca    vs#0 av1         R001 PQ: 0 ANSI: 5
[    3.661731] scsi 4:0:0:1: Direct-Access     Areca    vs#1 av2         R001 PQ: 0 ANSI: 5
[    3.661841] scsi 4:0:0:2: Direct-Access     Areca    vs#2             R001 PQ: 0 ANSI: 5
[    3.662726] scsi 4:0:16:0: Processor         Areca    RAID controller  R001 PQ: 0 ANSI: 0
```
How can I configure Ubuntu in order to access the 3 volumes above?

Thanks,

---

