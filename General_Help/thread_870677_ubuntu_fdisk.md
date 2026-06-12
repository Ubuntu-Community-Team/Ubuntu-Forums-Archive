---
title: "ubuntu fdisk?"
date: 2008-07-26
forum: General Help
---

### Post by tejaka on 2008-07-26
Hello,

I tried to install Ubuntu on IDE hard, and Ubuntu didn’t detect that. And then I tried with sata HDD, ubuntu could successfully install on that. 

Is there no way to install Ubuntu on IDE HDD?
My MB = MSI K9N6GM

Any help please….

Thanks.

---

### Post by plucky on 2008-07-26
> **tejaka said:**
> Hello,

I tried to install Ubuntu on IDE hard, and Ubuntu didn’t detect that. And then I tried with sata HDD, ubuntu could successfully install on that. 

Is there no way to install Ubuntu on IDE HDD?
My MB = MSI K9N6GM

Any help please….

Thanks.

Can you see the IDE drive in the BIOS,ie before the operating system boots?

Boot the Ubuntu Live CD to the desktop and then open a terminal using **Applications > Accessories > Terminal** and input the following command ```
sudo fdisk -l
``` That is lowercase L not a 1.

Post the output to the forum.

Thank you.

---

### Post by tejaka on 2008-07-26
yes BIOS detect IDE and already windows XP runs well on that.

when i typed 
```
sudo fdisk -l
``` -> nothing happened.
```
fdisk
``` -> typical options were given
```
fdisk /dev/hda
fdisk /dev/hda1

```  ->says unable to open...

also when i go to my computer from places manu, it only shows files system but not anything about IDE.

any idea please?

---

### Post by plucky on 2008-07-26
Does your IDE drive and DVD/CD drive share the same IDE channel?

If so are they on cable select or master/slave? Set the disk as master and the dvd as slave.

The "sudo fdisk -l" should have showed something,did you have the sata drive plugged in as well?

You should check your BIOS and see what settings there are for IDE and Sata drives.

---

### Post by tejaka on 2008-07-26
> **plucky said:**
> Does your IDE drive and DVD/CD drive share the same IDE channel?

If so are they on cable select or master/slave? Set the disk as master and the dvd as slave.

The "sudo fdisk -l" should have showed something,did you have the sata drive plugged in as well?

You should check your BIOS and see what settings there are for IDE and Sata drives.

actually there was a mistake with the direction of cable has plugged. because both HDD and DVD rom share same cable and it was upside down. when i charged it's direction, and booted from ubuntu live CD now, it shows IDE with all it's patrician...

hope now it will let me install ubuntu on it...
Thank you plucky...

---

