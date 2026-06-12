---
title: "Howto Install Software RAID 1 on Ubuntu 5.1 and boot from RAID"
date: 2005-11-19
forum: General Help
---

### Post by folker on 2005-11-19
I try to install Ubuntu 5.1 with Software RAID 1.
I've got a Dell SC1425 with 2 SATA disks.
During the installation I created 5 partitions on both disks formated as Linux Raid partition. (/boot / /tmp /var /home) and on both disks 1 swap partition.
After creating the partitions I created the Software RAID 1.
MD0 formated as EXT3 /boot
MD1 formated as EXT3 /
etc.
I finished the installation succesfully.
After the installation everything is working ok, but if I shutdown the system
disconnect harddrive 1 and boot again the system does not boot from disk 2.
What do I have to do to make both disk bootable?
Is this the right way to set up a Software RAID 1?

---

### Post by ubuntu_demon on 2005-11-19
I moved this thread. Please don't post questions in the customization section!

---

### Post by folker on 2005-11-20
Sorry, but can please anyone help me?

---

### Post by cylon359 on 2005-11-20
[QUOTE=folker]Sorry, but can please anyone help me?[/QUOTE]

Well, you probably have grub installed on the first harddrive, but not the second...

---

### Post by folker on 2005-11-20
[QUOTE=cylon359]Well, you probably have grub installed on the first harddrive, but not the second...[/QUOTE]

Ok but how do I install it on the second harddrive?

This is what I have tried, but I had an error in the first command:

grub> device (hd0) /dev/hda
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/hdb
grub> root (hd0,0)
grub> setup (hd0)

---

