---
title: "Finding XP Partition"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by nzkronic on 2009-03-13
Hi, I have recently have made some space to install a xp partition, after installing xp on the free space I messed up my bootloader, I have managed to fix it so I can access the grub boot menu and boot into ubuntu.

I need to find out how to find what partition my xp is installed on so I can enter the correct entry in the /grub/menu.lst file.

eg. 

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c69aa91d-d9b9-4054-8ef5-01b3c1dc20cd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c69aa91d-d9b9-4054-8ef5-01b3c1dc20cd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

and 

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

is there any commands I can use so I can choose the correct "hd0, hd1" I dont really know what the map commands are as well. 

Edit here is the command which may list something useful
 sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e74969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15562   125001733+  83  Linux
/dev/sda2   *       15563       18701    25214017+   7  HPFS/NTFS
/dev/sda3           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
kieran@AstroTrain:~$ 





Thanks, any help is appreciated.

---

### Post by meierfra. on 2009-03-13
title Windows
root (hd0,1)
chainloader +1

---

### Post by Mark Phelps on 2009-03-13
As seen above, you don't need the map commands because both OSs are on the same disk.

If the "root (hd0,1)" command doesn't work you can try "rootnoverify (hd0,1)" instead.  Sometimes it needs the latter version.

---

### Post by nzkronic on 2009-03-13
Thanks for that, will try them out soon.

---

