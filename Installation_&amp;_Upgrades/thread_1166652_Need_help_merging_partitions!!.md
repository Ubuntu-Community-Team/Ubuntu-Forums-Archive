---
title: "Need help merging partitions!!"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by bmfc187 on 2009-05-21
Ive been doing a LOT of reading and searching, so please dont flame me for starting a new thread, im trying to dual boot Jaunty and Windows Vista on a Compaq Presario f700, i have both system working and all, but i have a partition problem.  When i installed it i left the partition setting at default (2.4GB) and so NOW, after a lot of reading and searching and more reading, i have successfully shrank my windows partition and what i did was COPY my ext3 partition and pasted it over the unallocated space left over from the windows shrink, which i kinda thought was the same as merging them, but now i have two linux partitions and i wanna combine them and theyre next to each other, but i cant seem to get it to do what i want it to do, i have the Gparted liveCD, and heres the results of the fdisk....

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd23d125d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14997   120459036    7  HPFS/NTFS
/dev/sda2           17932       19457    12257595    7  HPFS/NTFS
/dev/sda3           17606       17931     2618595    5  Extended
/dev/sda4           14998       17605    20948760   83  Linux
/dev/sda5           17606       17909     2441848+  83  Linux
/dev/sda6           17910       17931      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
```someone please help me, all i want is for the two ext3 partitions to be ONE ext3 partition...

-BMFC

---

### Post by Sef on 2009-05-22
How did you shrink your vista parition?

---

### Post by bmfc187 on 2009-05-22
using Vistas built in patition manager.  but it doesnt mess with anything but fat/ntfs/and one other one i dont remember right this second, so i downloaded a couple of partition managers only to find that they, too, only mess with windows-based partitions.  they wont touch the ext3 patitions.  so i now have the Gparted liveCD and it works but theres no option to merge the partitions. i think my problem is that the first ext3 partition(dev/sda5) is (correct me if im wrong) a logical partition inside /dev/sda3, the extended partition?  and i want to merge this with the /dev/sda4 (a primary partition which was the leftover unallocated space from my windows C: drive, formatted to ext3) 
so i dont know whats possible right now, i tried to copy the /dev/sda5 into the unallocated space, hoping that would make it able to boot from the larger partition so i could format the small one and extend it, but it didnt work...any ideas?  

-BMFC

---

### Post by bmfc187 on 2009-05-23
UPDATE:  I have now successfully made my patitions they way i want them (I think).  i have about a 20g partition for ubuntu, plus the swap partition the windows C: and D: drives' partitions, and no unallocated space.  I deleted my linux partition with the grub loader once and got the 
```
GRUB error 22...
``` a couple times, but now I have working copies of the Ubuntu AND GParted liveCDs.  apparently, the first time i tried with the option in WUBi to try without installing...i never got the try option, it just skipped that part and went ahead and installed.  So now back to the current problem...when i go into Gparted it shows me exactly what i want to see...which is my enormous Windows Vista Partition, followed by an extended partition containing my 20g linux partition and approximately 1GB swap.  Then my approx. 12 or 14g NTFS recovery partition. thats GREAT.  I can live with all of that.  
But NOW, my question is this:  to get this all the way i wanted it i had to install ubuntu a total of 4 times...and, as a result, when grub boots up i get a list kinda like this, only prolly a little more technical...

Ubuntu
Ubuntu Recovery
memtest
Other operating systems:
Wnidows Vista loader
Windows Vista loader
Ubuntu
ubuntu recovery 
memtest
ubuntu
ubuntu recovery
memtest

sorry its so basic but im on my g/fs comp right now trying to get answers before i mess with anything else. anyways my question is, how do i remove all the entries FOLLOWING the Vista loaders?  I know for a fact that the first entry is the one that works for getting me into ubuntu, and its the 20GB patition i specified, so all i want is to know how to edit/add/remove these entries, anybody help me do that?


EDIT:  I edit my /boot/grub/menu.list and all those stale entries are gone!  thanks for....the think space.....

-BMFC

---

