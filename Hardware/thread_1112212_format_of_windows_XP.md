---
title: "format of windows XP"
date: 2009-03-31
forum: Hardware
---

### Post by sovitkumar on 2009-03-31
i want to format windows xp which is affected by virus...i want 2 know will format of XP effect ubuntu 8.04.if yes, is there any solution so that i can format XP without effecting UBUNTU. first OS i install is windows XP

---

### Post by jespdj on 2009-03-31
You can just format your Windows XP partition, that will not affect your Ubuntu installation - unless you installed Ubuntu with Wubi for example, instead of in a separate partition.

---

### Post by cariboo on 2009-03-31
You can use your Windows install cd to reformat your Windows partition, or you could install gparted in Ubuntu and then go to System-->Administration-->Partition Editor to format the partition. 

If you reinstall Windows you will have to repair grub after the installation. I use [thread=224351]this[/thread] howto when I have to repair grub.

Jim

---

### Post by ivanvajar on 2009-03-31
What if MBR is on Windows partition? He'll need to restore GRUB if that is the case also.

---

