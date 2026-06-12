---
title: "grub does not recognise one of the disks"
date: 2008-11-03
forum: General Help
---

### Post by chriskin on 2008-11-03
i have two disks currently on my laptop, the one that comes with it and an external one
i tried installing debian on the external, and the installation was ok, yet when i tried to reboot there was a problem with the boot loader

so, using the ubuntu live cd, i reinstalled grub, yet upon restart it could only recognise windows and ubuntu, not debian

is there any way to add debian on my boot options without having to install it on the same disk as the others?

---

### Post by caljohnsmith on 2008-11-03
Do you know which HDD you are booting on start up? How about first posting:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And please identify your partitions.

---

### Post by chriskin on 2008-11-03
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24563384    12281661    5  Extended
/dev/sda2   *    24578048   217948159    96685056    7  HPFS/NTFS  <--windows
/dev/sda3       217953855   239432759    10739452+  83  Linux  <--ubuntu
/dev/sda4       239432760   312576704    36571972+   7  HPFS/NTFS
/dev/sda5             126     4096574     2048224+  82  Linux swap / Solaris
/dev/sda6         4096638    24563384    10233373+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005bff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    39070079    19535008+  83  Linux <---debian
/dev/sdb2       143364060   488392064   172514002+   7  HPFS/NTFS



for the rest of it, is "missing etc" to be left like this ? 

cause it only gives 
christos@CNB:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
christos@CNB:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
christos@CNB:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump0000000 ff02                                   
0000002
christos@CNB:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump0000000 0000                                   
0000002

---

### Post by caljohnsmith on 2008-11-03
So can you boot into Ubuntu OK? Did you install Grub with Debian? You can check to see if Debian has a menu.lst with:
```
sudo mount /dev/sdb1 /mnt
ls -lR /mnt/boot
ls -lR /mnt/boot | grep menu

```
And please post the output of the above commands. If Debian has a menu.lst, then in your Ubuntu's menu.lst, you could add:
```
title Debian Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
And you can modify your Ubuntu menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Let me know how it goes or what problems you run into.

---

### Post by chriskin on 2008-11-03
i can boot on ubuntu just fine

it is debian i cannot boot in 

the bootloader is ubuntu's , i reinstalled it after debian cause debian's got me an error

i can edit menu.lst on ubuntu easily, but what am i supposed to write there?

(how i am going to check on debian if i cannot load debian at all?)

---

### Post by chriskin on 2008-11-03
i will not try to solve this any more, i will install debian on my first disk  :S

---

