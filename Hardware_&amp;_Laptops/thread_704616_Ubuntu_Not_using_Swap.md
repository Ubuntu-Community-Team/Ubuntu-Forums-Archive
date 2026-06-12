---
title: "Ubuntu Not using Swap"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by scienceman91 on 2008-02-22
I have about a gig of memory and every now and the it fills when i run several programs at once. But the swap isn't getting used. Fstab says that it is mounted as swap. But when i run a bunch of programs and open the system monitor everything is skyrocketed and swap is almost completely empty. about 1,000kb is used while the whole systems hangs and swap never goes up or down and the hd light on the laptop almost never lights. its a 5 gig swap that does nothing in ubuntu and works fine in suse. oh and im amd64

---

### Post by taurus on 2008-02-22
Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by scienceman91 on 2008-02-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=37ee0352-a252-4ae0-a864-a10159ee9cbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ACDE826BDE822E20 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=e3b8813b-9a1b-4a4b-89eb-0baf86e8b703 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
ean@ean-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        899188     728740     170448          0      24996     384856
-/+ buffers/cache:     318888     580300
Swap:      5164888      38464    5126424
ean@ean-laptop:~$ clear
ean@ean-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        899188     729588     169600          0      25040     384764
-/+ buffers/cache:     319784     579404
Swap:      5164888      38464    5126424
ean@ean-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=37ee0352-a252-4ae0-a864-a10159ee9cbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ACDE826BDE822E20 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=e3b8813b-9a1b-4a4b-89eb-0baf86e8b703 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
ean@ean-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00056399

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11821    94952151    7  HPFS/NTFS
/dev/sda2           18388       19457     8594775    7  HPFS/NTFS
/dev/sda3           11822       17744    47576497+  83  Linux
/dev/sda4           17745       18387     5164897+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2008-02-22
> 
ean@ean-laptop:~$ free
total used free shared buffers cached
Mem: 899188 729588 169600 0 25040 384764
-/+ buffers/cache: 319784 579404
**[COLOR="Blue"]Swap: 5164888 38464 5126424[/COLOR]**

You have your swap there so what do you mean that it doesn't work?

---

### Post by scienceman91 on 2008-02-22
oh its there and it should work it just doesn't ever get used. I can over load my mem and it still wont get used. Matter fact i have done so several times. It's there. It's mounted. the kernel just doesn't use it for some reason. i would like to know why and how to fix it

---

