---
title: "Problems installing with VMWare Workstation 7"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by gjunderhill on 2009-11-03
Hi guys,
 
I'm trying to install Ubuntu 9.10 into a VM, using WMWare Workstation 7 on a Windows 7 host.
 
The problem is that, just after I hit 'Install Ubuntu', i get a ton of messages saying 'unable to read page, unable to fragment' etc.. I have managed to take a screenshot of the very start of these messages in case it helps.
 
I have tried different HDDs, (SCSI and IDE) but it's the same problem.
 
Any ideas?
 
Thanks,
Gary

---

### Post by Martin_sensei on 2009-11-03
Hello,

Although I don' have a Win 7 host, I have managed to install Ubuntu 9.10 on VMware 7, I just let easyInstall do all the work.  

My Hard Disk is SCSI on the guest.  I did get some strange erors during installation, but a working Ubuntu emerged at the end.

I don't think Ubuntu 9.10 is supported by VMware though.  Are you able to install 9.04?

---

### Post by gjunderhill on 2009-11-03
Hi,
 
that's interesting then.  I've also tried this using a Vista host, and VMWare 6.5, and I get the same problems.
 
How long did it take you to install?  If I leave it along, the Ubuntu screen appears, the screen then goes black and I just get the busy cursor - even after 30 mins.
 
How odd!

---

### Post by konkara on 2009-11-03
I was able to install 9.10 in Vmware 7. However, I am unable to mount vmware tools. 9.04 worked just fine, but 9.10 says that iso9660 is an unrecognized type.

I get the same iso9660 error if I try to mount an iso while in the Ubuntu 9.10 vm.

---

