---
title: "I made vista partition larger and Linux partition smaller"
date: 2008-11-11
forum: General Help
---

### Post by techhero2 on 2008-11-11
Hey smart people. I made my Linux partition smaller then made my Vista partition larger with the Live cd Gparted. (I have been successfully dual booting for like 4 months.) I think I was using EasyBCD to boot?? not sure?? definitely not grub though. When I rebooted after shrinking/growing, I didn't get a selection screen, but a blank screen and a blinking cursor. I went back to Gparted and moved the boot flag (which was on the vista) to the linux. Kubuntu booted straight up with no grub or nothing. Then, I ran the vista startup recovery deal-ee-o and it "fixed the problem". Back to blinking cursor. I went into Gparted a third time and moved the flag to linux (it was on vista b/c the recovery moved it). I then got a grub menu which didn't have vista. I ran the startup recovery from the vista cd again and I still get grub now???? This is where I am. Here is my fdisk command

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   83  Linux
/dev/sda2   *         638       14405   110591460    7  HPFS/NTFS
/dev/sda3           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

---

### Post by adult swim on 2008-11-11
if you dont mind to use grub you can add vista to it by booting into ubuntu, and running ```
kdesu kate /boot/grub/menu.lst
``` then add 
```
title		Vista
root		(hd0,1)
chainloader	+1

``` to the end and save the file.  then reboot and you should be good

---

### Post by techhero2 on 2008-11-11
Didn't work, still get blinking cursor.

---

### Post by TeXtonyx on 2008-11-11
I think Gparted is the best tool to resize Linux partitions and 
Vista is the best tool to resize the Vista partition, adding the
unallocated space that Gparted created. I see about 10 posts a
month on this forum about the Windows boot sector getting damaged
when Gparted resizes it, usually during the live cd install, and
usually when Windows is getting shrunk. I'm not denigrating Gparted
but Windows software engineers have access to proprietary code and
Gparted was not built to resize Windows, but the Vista resizer is. 

I think you should try the fixmbr and fixboot commands again from
the Vista recovery console, bootrec. Testdisk also has a tool to
restore the backup boot sector; not sure if that will help. 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)
 NTFS Boot sector recovery, towards the bottom there's a screenshot

[http://ubuntuforums.org/showthread.php?t=975789](http://ubuntuforums.org/showthread.php?t=975789)
Post #2 references the steps to take.

---

