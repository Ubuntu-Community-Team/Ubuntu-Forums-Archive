---
title: "[SOLVED] Ubuntu boots randonly from wrong Hard drive"
date: 2008-08-08
forum: Hardware
---

### Post by g1rnz on 2008-08-08
Hi all, I have a PC with three Hard drives Master and two Slaves, Master has Ubuntu on and the first Slave has a cloned copy of the first as a backup and is bootable. my grub loader has an entry for both hard drives. however when booting if I select the master from the Grub list it will often but not always boot the slave. if I restart and try again it will then boot the correct hard drive ie the master. Any ideas what is the cause of this?

Graham

---

### Post by logos34 on 2008-08-08
> **g1rnz said:**
> when booting if I select the master from the Grub list it will often but not always boot the slave. if I restart and try again it will then boot the correct hard drive ie the master. Any ideas what is the cause of this?

Identical UUIDs?

When you clone a drive, the UUID is copied too.  If the menu.lst entries have duplicate kernel lines ('root=UUID=xxxx...') , that might be what's causing the mixup

---

### Post by g1rnz on 2008-08-08
> **logos34 said:**
> Identical UUIDs?

When you clone a drive, the UUID is copied too.  If the menu.lst entries have duplicate kernel lines ('root=UUID=xxxx...') , that might be what's causing the mixup

Both Hard drives had the Same UUID I had changed the menu.lst to show /dev/sdx instead of UUID but it still caused problems. I have now used tune2fs -u ramdom <device> to change one of the drives UUID and this seems to have solved  the problem. The only issue now is that as I wish to backup the Master drive in the future with cloneziller I will have to change the UUID afterwards.

Thanks for help.
Graham

---

