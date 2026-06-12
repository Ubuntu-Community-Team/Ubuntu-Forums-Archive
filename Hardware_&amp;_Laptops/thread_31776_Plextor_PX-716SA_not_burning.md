---
title: "Plextor PX-716SA not burning"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by IndieRockSteve on 2005-05-04
howdy all, upgraded my computer, new mobo has SATA figured its time to get a DVDRW drive. Noticed Plextor has this drive so I bought it. Now I can't get Ubuntu to burn with it, growisofs just freezes(honestly haven't tried cdrecord or cdrdao yet). I was wondering if anyone else has this drive and if its working for them?

Thanks!

---

### Post by alastair on 2005-05-04
No idea. It is always useful to look atthe log file for boot and see if the kernel recognises it though i.e. check :

/var/log/syslog

for CD/CDRW messages.

---

### Post by IndieRockSteve on 2005-05-04
I get:
May  3 20:31:18 localhost kernel: SCSI error : <0 0 0 0> return code = 0x2
May  3 20:32:44 localhost kernel: ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x20
May  3 20:32:44 localhost kernel: SCSI error : <0 0 0 0> return code = 0x2

in the kern.log
the drive works as a CD/DVD rom drive.

---

### Post by IndieRockSteve on 2005-05-05
bump

---

### Post by IndieRockSteve on 2005-05-09
reported as bug to kernel team.

---

### Post by RicgorE on 2005-05-09
My PX-716A works well. I use Hoary with GDM. K3B to burn. SATA issue maybe? I've read  more than one post related to problems with sata optical drives and linux.How new is the drive? Can it still be exchanged for a ata one?

---

### Post by IndieRockSteve on 2005-06-02
I think it is SATA. hopefully the kernel team is working on the issue. I really don't want to trade it in for an ATA drive(trying to slowly move to all SATA) and already have a single side Liteon DVD burner that I can use until they fix it.

which hopefully will be soon...

---

