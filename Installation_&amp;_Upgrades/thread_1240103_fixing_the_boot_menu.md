---
title: "fixing the boot menu"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by techrascal on 2009-08-14
hello all..

problem: grub showed error 17 , to access windows i used windows vista cd to fixmbr..so no longer able to access linux partitions in ext hd.

some specs:
i am working on windows and cant put the fdisk output..so the information necessary is that i have windows on 60 gb hard drive of laptop...
on an external hard disk i have ubuntu 9.04, fedora11, debian5...
i have live cd of ubuntu 8.10 in hand and fedora 11 cd in hand..

help.....need to fix grub so that it is able to show all these os-es in the selector menu .

thanx in advance

---

### Post by presence1960 on 2009-08-14
Plug in the external drive. Boot the Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo fdisk -l
``` that is a lowercase L at end! post the output of that command back here.

---

### Post by techrascal on 2009-08-14
fdisk -l output:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7026    53116528+   7  HPFS/NTFS
/dev/sda2            7027        7752     5488560    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe00766e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        5106     1951897+  82  Linux swap / Solaris
/dev/sdb3            5107        9969    39062047+  83  Linux
/dev/sdb4            9970       19457    76212360    5  Extended
/dev/sdb5   *        9970       15069    40960000   83  Linux

i was also getting error 21 earlier....i suppose i made a mistake in placing grub....the device boot should not have been sdb5...
thnx in advance...

---

### Post by ronparent on 2009-08-14
You probably will want to boot from the external drive only when present on boot. 

To fix grub to do that, boot from a live cd, insert the external drive, and, start a terminal. In the terminal enter the fowing sequence of commands:

**sudo grub**

At the grub prompt enter:

**find /boot/grub/stage1**

Use the out put of the above to find your ubuntu entering as follows:

[B]root(hdx,y)
setup (hdx)[/B]

Make sure you boot order is set to try booting from the external drive forst. On the next boot you should get the grub menu allowing you to boot to any of your installed systems. This will probably bring you back to whre we started with a grub erro in finding windows. You will then have to **sudo gedit /boot/grub/menu.lst** to change the windows location, probably to (hd1,0). Once all this is done you should be able to boot from the external drive and find any of your installed OS's. When the external drive isn't present you should be able to boot to windows again without having to restore the MBR. Goood luck and keep us posted if you run into problems.

---

### Post by presence1960 on 2009-08-14
+1 ron

---

### Post by techrascal on 2009-08-14
one more question : i am getting three outputs for find /boot/grub/stage1
(hd1,0)
(hd1,2)
(hd1,4)

which one shd i choose...

---

### Post by presence1960 on 2009-08-14
> **techrascal said:**
> one more question : i am getting three outputs for find /boot/grub/stage1
(hd1,0)
(hd1,2)
(hd1,4)

which one shd i choose...
from fdisk -l output:
(hd1,0) is sdb1
(hd1,2) is sdb3
(hd1,4) is sdb5

use whichever partition your ubuntu is on. It looks like maybe sda5 because it has a boot flag. Just to be sure, what is on those partitions? If you aren't sure download the boot info script in my signature line to desktop. Open a terminal and run this command > sudo bash ~/Desktop/boot_info_script*.sh This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here.

---

### Post by techrascal on 2009-08-15
thanks a lot  for the help.. it fixed the problems....
thanks to presence and ron...
i'll get back to you if i face any more issues....

---

### Post by presence1960 on 2009-08-15
Glad you got it working! Enjoy Ubuntu.

---

