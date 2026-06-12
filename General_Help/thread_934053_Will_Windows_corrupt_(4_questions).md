---
title: "Will Windows corrupt? (4 questions)"
date: 2008-09-30
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-30
okay, so i have a 160Gb HDD, 30Gb i have given to XP as NTFS, the remaining 130Gb is unpartitioned.

Is it possible to put in the Ubuntu LiveCD and create space for ubuntu to go on?

also, do i need /home space on ubuntu?

and  will i have to make a /boot partition ?

Will i get the GRUB boot loader with windows as an option by default??


thanks!

---

### Post by lisati on 2008-09-30
The normal installer provided on the LiveCD gives you the opportunity to make some choices as to where to put Ubuntu and how existing partition(s) should be resized. Be sure to read the options provided carefully.

The installer can cope with leaving Windows on your system, and will automatically give Windows as an option in the Grub menu if you choose to leave Windows on your system.

It's also a good idea to make a backup of important data and to defrag your Windows partition before starting.

---

### Post by Thyssenkrupp on 2008-09-30
Awesome, cheers,

So do i need to make /boot + /home space?

---

### Post by lisati on 2008-09-30
> **Thyssenkrupp said:**
> Awesome, cheers,

So do i need to make /boot + /home space?

Because I haven't had the need (so far) to set my installation differently from the defaults, other forum members may be in a better position to give a useful opinion.

---

### Post by Jouke74 on 2008-09-30
Okay, so i have a 160Gb HDD, 30Gb i have given to XP as NTFS, the remaining 130Gb is unpartitioned.
Is it possible to put in the Ubuntu LiveCD and create space for ubuntu to go on?

>> Yes, just make sure you choose the right empty 130 GB partition for Ubuntu to install on. DON'T select use whole disk (which will erase Windows). You can also make and assign  partitions manually yourself as you wish. 

Also, do i need /home space on ubuntu?

>> The only two partitions you really need are /root and /swap, the rest is optional. It could be handy to have /home separate as well, in case you want to reinstall often (never used it myself). 

and  will i have to make a /boot partition ?

>> Not required. Make sure you have GRUB install on the master boot record of the harddisk from which you are booting. In almost all cases it will detect windows automatically and add it to the list of operating systems. You will then have a dual boot computer.

Will i get the GRUB boot loader with windows as an option by default??

>> Yes, otherwise it's quite easy to add.

thanks!

>> You're welcome.

PS1! In all cases make a backup of everything important before you start doing this!!! I don't want to know how many people accidentally take the whole disk for Ubuntu, use the partitioner wrong etc...

PS2! During partitioning, add the existing Windows partition at a mount point (e.g. media/windows) to have it shown and mounted in Ubuntu as well at startup.

---

