---
title: "External USB Hard Drive  Stalling Issues"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by welders4linux on 2007-01-01
I am having problems with my External Hard USB hard Drive,

*have upgraded to 6.10
*Read USB HD is fine
*Write to USB HD is fine if small files are being transfered
*Write to USB HD stalls on larger files, typically over a few megabytes.

sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2267    18209646   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16759   134616636    7  HPFS/NTFS
/dev/sda2           16760       20023    26218080   83  Linux


this is my fstab (my last entry did not work)

android@android-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0732a21c-e0bb-4675-84a0-6418dc46b3f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0acf7358-b09e-4a12-b649-c089f3d1f3b6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#  /dev/sda2   /media/usbdisk  auto    users,gid=users,umask=0000,defaults

Just some newbie thoughts:

could you somehow slow down the transfer perhaps ?  could cache be used in this case?
 
Ive read this link: [http://www.justlinux.com/forum/showthread.php?t=119463](http://www.justlinux.com/forum/showthread.php?t=119463) and others like it
and thought it could be something in the actual kernel.

I love Linux and praise it everyplace I go.  Its a real thorn in the side to know Im actually having problems with something that Windows has no problems whats so ever.

thanks in advance for any help you can lend.  A hero cookie goes to the person that can solve this for me! :-D

---

### Post by pepevilluela on 2007-05-14
I have same problem:
I could mount my IOMEGA external ntfs hard disk in edgy and copy large files like videos. Since y updated to feisty I can mount with ntfs-3g, see what's inside, but when i copy my disk looks as it were frost, tells me that it will take 129 hours, and nothing moves in progress bar. Anybody can solve it?

---

