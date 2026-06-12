---
title: "deleting ubuntu"
date: 2008-11-19
forum: General Help
---

### Post by Phyrax on 2008-11-19
I made a partition of my hard drive for ubuntu, but i don't really use it all that much anymore, how can i delete ubuntu and get my partition back to 1 thing? btw i use vista home premium.

---

### Post by darco on 2008-11-19
In Windows,right click Computer, choose Manage. Look for Disk Management. You then can delete the partition....
If you are unhappy w/Ubuntu, try Linux Mint.....

darco

---

### Post by volaer on 2008-11-19
If you have installed it in a dual boot system, boot windows. Go  to your drive C, and look for UBUNTU folders. Click it and hopefully you will find uninstall. Click uninstall and it will be uninstalled. After uninstalling, you can delete the folders of ubuntu completely.

Just a note, if you are to delete a partition, your vista might be affected and might be deleted at the same time. If I were you, if you are really to delete a partition, I would back up all my files, delete all the partition, and then reformat. 

But how said, you will leave our community... Anyway, hope you will still find your way back to ubuntu. God bless.

---

### Post by EvilRobotDrew on 2008-11-19
easy!

pop in a live CD, choose "run Ubuntu without changing your computer"

once the LiveCD is booted, go to System -> Administration -> Partition Editor

choose your harddrive, select your ubuntu partition, select delete, choose your windows partition, and expand it to take over the newly Unallocated space

click "Apply" know that expanding an NTFS partition is probably going to take a while, i would go grab a coffee, 

that should be it, reboot the computer, remove the LiveCD and enjoy Windoze

---

### Post by Phyrax on 2008-11-20
ok i uninstalled it, and it gave me a whole lot of space back, but it still has the dual boot option when i boot my pc. how do i get rid of this?

---

### Post by TeXtonyx on 2008-11-20
If you are getting your boot menu options from Vista's bootloader
and not grub, the easiest way is to download a free program named
Easybcd. Run that and remove the Ubuntu entry. Easybcd is like a
Vista bootloader menu editor.

---

### Post by Phyrax on 2008-11-21
> **TeXtonyx said:**
> If you are getting your boot menu options from Vista's bootloader
and not grub, the easiest way is to download a free program named
Easybcd. Run that and remove the Ubuntu entry. Easybcd is like a
Vista bootloader menu editor.

yeah, it worked, thanks. :)

---

