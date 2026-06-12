---
title: "plz help me with grub/windows"
date: 2008-10-12
forum: General Help
---

### Post by victorvelasco1 on 2008-10-12
hi i am a lil new to ubuntu, i know some but not much

i have a computer that is like 2 years old with 200gb hd

it was only windows xp..

but i added xubuntu and then ubuntu

so now in grub 

windows does not show :confused:

if i type   sudo fdisk -l 

this shows :

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             625        1110     3903795   83  Linux
/dev/sda2   *        1111       24321   186437160    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3               1         624     5012248+  83  Linux

Partition table entries are not in disk order



can someone help me get windows back

my email is "victor_velasco_1@yahoo.com"

---

### Post by victorvelasco1 on 2008-10-12
if u need more info
just tell me how and where to get it..:popcorn:

---

### Post by Sam on 2008-10-12
Add at the end of the file /boot/grub/menu.lst
```
title		Windows XP
lock
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by raywood on 2008-10-12
I'm sure you'll get tons of help.  But in case you don't, I worked through this in great detail.  See [http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-grub-and-acronis-true-image.html](http://raywoodcockslatest.blogspot.com/2008/09/ubuntu-grub-and-acronis-true-image.html)

---

### Post by victorvelasco1 on 2008-10-12
but hey it wont let edit the menu.list

it says 

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Sam on 2008-10-12
> **victorvelasco1 said:**
> but hey it wont let edit the menu.list

it says 

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by inxygnuu on 2008-10-12
same thing happened to me:(. I have vista back now, but I lost all of my stuff:( although, it did have a serious Trojan virus on it...

My recommendation would be to; at last resort, backup all of your important files on it (somehow) and insert a backup disk and start a new. This is only at last resort though.

---

### Post by victorvelasco1 on 2008-10-12
i did what u said
and all that happend was that
windows now appears on grub
but if i select it..
it just says 

starting...
then it says GRUB

and gets stuck...

---

### Post by Sam on 2008-10-12
In Ubuntu, can you access the windows partition ? Please post the output of```
cat /etc/fstab
```
and
```
cat /etc/mtab
```

---

### Post by victorvelasco1 on 2008-10-12
victor@victor-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee4f660b-d12e-497a-8ad0-25eec0294bef /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


victor@victor-desktop:~$ cat /etc/mtab
/dev/sda3 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/victor/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=victor 0 0


its that right??

---

### Post by Sam on 2008-10-12
Try:
```
sudo mkdir /mnt/windows
sudo mount /dev/sda2 /mnt/windows/ -t ntfs -o defaults,umask=007,gid=46
```

Can you see your Windows partition in /mnt/windows ?

---

### Post by TeXtonyx on 2008-10-12
OP wrote that XP got as far as "starting". Did it really say "starting up"? 
If so, after you try the other ways of fixing this, try this testdisk method as a sort of last resort.

 Re: XP Won't load.
I've seen Testdisk fix this Windows Starting Up hang problem. Perhaps somebody reading
has some expertise with the Testdisk program. Otherwise, I think a repair installation
using the XP install cd will be needed. I borrowed this advice from meierfra about using
Testdisk. sda is the first drive and sdb is the second drive and so on.

"You might try testdisk to rebuild the Boot sector:

Code:

sudo apt-get install testdisk
sudo testdisk /dev/sda

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"

TeX: If it reports "Extrapolated boot sector and current boot sector are different."
Then "Write" the rebuild and it hopefully will report they are now the same, so reboot and
see if the Rebuild fixes the problem.

---

### Post by victorvelasco1 on 2008-10-12
oh and no i cant access anything

---

### Post by victorvelasco1 on 2008-10-12
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS           1110 150  1 24320 239 63  372874320 [HP_PAVILION]

filesystem size           372874320
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               23304644
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

---

### Post by caljohnsmith on 2008-10-12
Do you have a Windows Install CD, victorvelasco1? If you do, boot that up, go to the "recovery console" and run:
```
fixboot
chkdsk /r
```
And let me know if that changes anything.

---

### Post by victorvelasco1 on 2008-10-12
no i dont have one....

---

### Post by victorvelasco1 on 2008-10-12
i got rid of xbubtu
and
ok i did something tony told me to do
 and now it says 
windows and ubuntu in grub
but only ubuntu works
if i pick windows...

it says 

starting up...
hard disk error

---

### Post by *B* on 2008-10-12
Ok, Im sure there are others who know a LOT more than me, but I had the same exact problem getting the boot config set up right on an XP system I wanted to add Ubuntu to. After much trial and error, here is what worked the easiest for me.

1. Unhook the drive with XP on it altogether.
2. Hook the drive up that you want to load Ubuntu on, to the Master/Primary IDE/SATA port, so no other disk is hooked up.
3. Load Ubuntu normally with just the one disk hooked up. This will make sure you cant load grub elsewhere and it will also ensure you dont altar the MBR on the XP drive.
4. After you have Ubuntu loaded, working, and booting properly, hook the XP drive back up as secondary drive.
5. Boot the computer to Ubuntu and set whatever parameters you need in fstab and mtab for recognizing and mounting the XP drive.
My fstab:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=20845829-5bba-4832-b79b-97ef669c5c5d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=80327dc6-168c-4709-91e1-f908e1852a67 /home ext3 defaults 0 2
# Entry for /dev/sda4 :
UUID=E25E-D7C0 /media/hdb4 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda3 :
UUID=a72dc691-49d5-4143-b23e-a9c5705da5c0 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdb1 /media/160GB\040WD ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
Notice the first 4 entires (sda1 - sda4) are my master disk with Ubuntu and 4 partitions, and the last entry (sdb1) is the XP drive with the single partition on it

My mtab:
```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sda2 /home ext3 rw 0 0
/dev/sda4 /media/hdb4 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sdb1 /media/160GB\040WD fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
```
again, you can see the different drives.
6. Reboot Ubuntu and make sure the XP drive is visible and configured correctly.
7. Edit etc/boot/grub/menu.lst and add your XP drive to the list of drives that will be recognized and bootable. Make sure the parameters are set right, as grub starts at 0,0 and fstab & mab start at a1. This seems extremely silly to me and Im sure it causes a LOT of problems, but thats how it is. In other words, my sda1 root partition in mtab & fstab would be listed as hd0,0 in grub. The system sees the root partition of my first drive as sda1... "a" for the first/master/primary drive and "1" for the first partition on that drive. That is how it shows up in mtab & fstab (sda1 - sda4). Grub has to list that same drive and partition as hd0,0 with "0" being the first/primary/master disk and "0" for the first partition on that disk. sda2 would then be hd0,1 and so on and your secondary XP disk would be sdb1, but listed in menu.lst as hd1,0

Here are my bootable entires from menu.lst:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title           XP Pro 32Bit
rootnoverify    (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title		Xen 3.1 / Ubuntu 8.04.1, kernel 2.6.24-19-xen
root		(hd0,0)
kernel		/boot/xen-3.1.gz
module		/boot/vmlinuz-2.6.24-19-xen root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro console=tty0
module		/boot/initrd.img-2.6.24-19-xen
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Xen 3.1 / Ubuntu 8.04.1, kernel 2.6.24-17-xen
root		(hd0,0)
kernel		/boot/xen-3.1.gz
module		/boot/vmlinuz-2.6.24-17-xen root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro console=tty0
module		/boot/initrd.img-2.6.24-17-xen
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=20845829-5bba-4832-b79b-97ef669c5c5d ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```
Just remember the default boot partition will be whatever one is listed first.
8. When you reboot, you should have XP listed in your boot options in grub and it should be bootable.
9. Now, the good part......... if in the future you say "screw XP, I am going Ubuntu exclusively".... all you have to do is unhook the secondary drive that has XP on it, and remove the entires from Menu.lst, fstab & mtab. If you decide to go back to XP exclusively, all you have to do is remove the Ubuntu drive, switch the XP drive to Master/Primary and boot. Remember, the MBR on the XP disk was unaffected, so you can boot to it anytime like that.

Hope this helps.

---

