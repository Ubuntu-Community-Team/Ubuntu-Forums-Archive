---
title: "Copying old harddrive to new bigger one"
date: 2008-07-31
forum: General Help
---

### Post by Xpyd3r on 2008-07-31
I have a 13 gig harddrive in my server, but I want to upgrade to a bigger harddrive without loosing all the programs and settings, as I don't want to have to reinstall everything.  So is there a way to make a complete copy of the harddrive onto a slave, then swap the master with the slave and reboot and have everything run as if the harddrive never changed in any way except for size?

---

### Post by tamoneya on 2008-07-31
Use the dd command.
```
dd if=/dev/sda of=/dev/sdb
```
You may have to edit fstab to correspond to the new UUIDs.

---

### Post by logos34 on 2008-07-31
I'd recommend the dd command.  If you do the whole disk (vs. a partition) it will even copy the MBR.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

>  Cloning an entire hard disk: 
     Code:
     dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror 
/dev/sda is the source. /dev/sdb is the target. [COLOR=red]Do not reverse the intended source and target.[/COLOR] It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

It copies EVERYTHING--including the UUID.

---

### Post by tamoneya on 2008-07-31
> **logos34 said:**
> I'd recommend the dd command.  If you do the whole disk (vs. a partition) it will even copy the MBR.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)



It copies EVERYTHING--including the UUID.

Oh i didnt realize it did the UUID.  Thats nice.

---

