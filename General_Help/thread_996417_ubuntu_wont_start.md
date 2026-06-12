---
title: "ubuntu wont start"
date: 2008-11-28
forum: General Help
---

### Post by computerwiz on 2008-11-28
ok i have ubuntu 8.04 and it wont boot, i had to tern off my computer without doing the shutdown process and not when i try to boot ubuntu i just get a black screen 

note: im runing ubuntu of a external hard drive & iv been getting grub error 17 and 21

---

### Post by Afkpuz on 2008-11-29
It's cause grub is looking for a hard drive address that has changed.  It's your external hdd's fault.  You need to repair the grub bootloader.

---

### Post by computerwiz on 2008-12-01
so do i go in ubuntu recovery mode?

---

### Post by Cyhawk on 2008-12-01
> **computerwiz said:**
> so do i go in ubuntu recovery mode?

You can start up the LiveCD again, open a console and type

grub-install --recheck /dev/sda1

Where /dev/sda1 is the device you have. (Could be hd@# @ == Letter, # == partition number, so like hda1 for partition 1 on the first IDE drive, works with same with SATA devices beginning with sd@#)

If that shows up, the problem is your boot order in the BIOS. (just change to the correct hard drive and startup)

If it doesn't, you can run grub-install /dev/sda1 and it will repair it for you.

-----------
Course, if this is all too much, you can just re-run the Ubuntu install which will do it too. (Make sure to remove any external drives/USB drives beforehand, sometimes it makes things screw up depending on the hardware you have)

---

### Post by computerwiz on 2008-12-02
could terning my computer off before shuting down have done this?

---

