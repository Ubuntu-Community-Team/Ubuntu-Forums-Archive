---
title: "Making a bootable clone backup"
date: 2008-10-26
forum: General Help
---

### Post by rmcellig on 2008-10-26
On the PC side, I used Norton Ghost to do a clone image of my drive. On the Mac side I use Superduper. Is there such a best for Ubuntu? I would like to if possible make regular bootable backups of my drive.

---

### Post by cariboo on 2008-10-26
If it needs to be bootable, have a look here:

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

This should do what you need.

Jim

---

### Post by C.S.Cameron on 2008-10-26
You can clone drives in Ubuntu simply using the dd command.

dd if=/dev/hda of=/dev/hdb

Before proceeding confirm that hda is the partition or disk you wish to clone from and hdb is the partition or disk you wish to clone to.

The new partition will be bootable if the old one is.

---

### Post by lsutiger on 2008-10-26
or you could use clonezilla
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ragtag on 2008-10-26
dd can also be used with netcat, to clone a machine over lan, though this is a slightly more complex.

---

### Post by jerome1232 on 2008-10-26
Nobody has mentioned PING yet! (Part Image is Not Ghost)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Although I second DD it's impervious to file systems, it just copies everything bit for bit.

---

