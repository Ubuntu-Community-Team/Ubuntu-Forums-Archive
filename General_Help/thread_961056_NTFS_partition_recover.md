---
title: "NTFS partition recover"
date: 2008-10-27
forum: General Help
---

### Post by XProgrammer on 2008-10-27
I totally screwed up my windows partition mistakenly when i install Ubuntu. Instead of choosing /dev/sda3 for load loader installation, i given /dev/sda1 which is windows vista partition. I could recover Windows Vista partition and HP backup partition using "testdisk" tool. I can mount C: drive on ubuntu and all files are intact. But, HP backup partition mounts and no files are there. but used : 3GB free 8.5GB it says. Looks, NTFS is corrupted. How can i recover HP backup partition?. 
After recovering Windows Vista partition using testdisk, still I'm not able to boot into windows Vista using grub. I added below entry.

title Windows Vista
rootnoverify (hd0,0)
makeactive
savedefault
chainloader +1


When i try get into windows vista, I got below message
Starting up ...
GRUB

and hands.

Can you someone please help me?. 

Thanks.

---

### Post by XProgrammer on 2008-10-29
Booted via Windows Vista Recovery Disk and recovered it. 

Ubuntu rocks.. Everything works out of box unlike windows , everything needs to install driver,driver, driver from user.

---

