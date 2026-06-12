---
title: "External RAID5 on SCSI controller in Gutsy"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by edeca on 2008-01-15
I have a RAID5 external disk array on a SCSI controller.  On the same controller is a tape changer on another channel.  All worked fine in Feisty.

I have just upgraded to Gutsy and it appears that the disk array is no longer recognised.  The SCSI controller is fine, the tape changer is recognised on the other channel but the disk array has no sdX entry in /dev and there is no mention of it in dmesg.  Running the server from an older livecd works fine, the disk array is recognised and I can mount it.

I haven't compared the output of lsmod between the two installs yet, but was wondering if anybody knew why this would be.  Was any supported dropped in Gutsy?

---

### Post by edeca on 2008-01-23
This is now quite a problem for me.  I have tried a Dell PERC controller and an LSI controller, neither work.  An older Kubuntu livecd recognises the external SCSI array fine.  Before the upgrade, Feisty recognised the disk array fine.  Gutsy does not recognise the disk array.

As I need this machine in service, I restored Feisty from the x86 server install CD as a fresh install.  The setup recognised the external array and allowed me to assign it a mount point.  However, when booted into the fresh system (no changes made) the external array is no longer recognised.

Am I missing any packages or modules which I require for this?

---

### Post by edeca on 2008-01-23
This now works after I replaced linux-image-2.6.20-15-server with linux-image-2.6.20-15-generic.  As neither has /proc/config.gz compiled in, I cannot easily compare the differences.

At some point I will compare the configurations from the source packages and see what is different.

---

