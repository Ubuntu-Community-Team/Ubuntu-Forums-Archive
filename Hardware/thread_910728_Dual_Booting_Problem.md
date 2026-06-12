---
title: "Dual Booting Problem"
date: 2008-09-04
forum: Hardware
---

### Post by Morgoroth on 2008-09-04
hope this is the right place, if not feel free to move :)

i currently have just ubuntu on my laptop, and have been trying to dual boot it with XP. ive partitioned the drive in gparted (using the live cd) and formatted said partition to NTFS, but when i boot from the XP disk, and after a few menus when it goes to install it says it cant detect any hard drives. (i also tried it with the partition unallocated, this had the same results)

anyone know how to fix this? or a better way of dual booting?

---

### Post by Bakon Jarser on 2008-09-04
Sounds like you might be using a SATA hard drive.  Win XP can't detect SATA hard drives by default.  You have to load the drivers onto a floppy and during install you will see a message that says something like press f6 now to install drivers for mass storage devices.  I don't remember exactly how to do it.  

If your hard drive isn't SATA then I don't know what the problem is.

---

### Post by Morgoroth on 2008-09-04
that could be it- where could i find out about the drivers?

---

### Post by Bakon Jarser on 2008-09-04
My SATA drivers came with my motherboard.  Google probably knows where yours are.

---

### Post by Morgoroth on 2008-09-05
right, so ive now got XP on the partition and working- ive been following these instructions:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)
and after completing them i have the option of both OS's on the boot menu, but when i select ubuntu, it doesnt boot (will stay on the loading screen, forever loading)

any ideas of what to do?

---

