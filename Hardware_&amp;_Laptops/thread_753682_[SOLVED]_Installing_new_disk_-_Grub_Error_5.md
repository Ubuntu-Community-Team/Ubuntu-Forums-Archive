---
title: "[SOLVED] Installing new disk - Grub Error 5"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by nwr222 on 2008-04-13
I am trying to install a new SATA disk.  Ultimately I want to move my existing install to the new disk, but I have some basic booting / hardware issues to get past first.
If I boot with the new disk connected I get
> GRUB loading, please wait
Error 5
I have a dual boot system - my GRUB menu.lst looks like this
> title           Ubuntu 7.10, kernel 2.6.22-14-generic 
root            (hd1,6) 
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f4e48c22-e046-4350-9544-ac10aeb230a4 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic 
quiet 

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root            (hd1,6) 
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f4e48c22-e046-4350-9544-ac10aeb230a4 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic 

title           Ubuntu 7.10, memtest86+ 
root            (hd1,6) 
kernel          /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title           Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title           Microsoft Windows XP Professional 
root            (hd0,0) 
savedefault 
makeactive 
chainloader     +1 

My fstab looks like this ...
> # /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sdb7 
UUID=f4e48c22-e046-4350-9544-ac10aeb230a4 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/sda1 
UUID=D638265F38263F3D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1 
# /dev/sda2 
UUID=0E3CD2383CD21B13 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1 
# /dev/sda3 
UUID=A8A0EA58A0EA2D0E /media/sda3     ntfs    defaults,umask=007,gid=46 0       1 
# /dev/sdb5 
UUID=7644E31944E2DB3F /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1 
# /dev/sdb6 
UUID=23a4390e-a64e-4670-8ce8-f56123f95658 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0 
/dev/sdb8       /home     ext3    nodev,nosuid 0 2 
#  UUID=8205a6d5-efcc-401e-895c-7df8e9ff4300 /media/sdb8 ext3 nodev, nosuid 0 2



> neil@neil-desktop:~$ sudo lshw -C disk 
  *-cdrom                 
       description: DVD writer 
       product: DVDRW1616N 
       vendor: TDK 
       physical id: 0.0.0 
       bus info: scsi@6:0.0.0 
       logical name: /dev/cdrom 
       logical name: /dev/dvd 
       logical name: /dev/scd0 
       logical name: /dev/sr0 
       version: 2.C8 
       serial: [TDK     DVDRW1616N      2.C804100400 
       capabilities: removable audio cd-r cd-rw dvd dvd-r 
       configuration: ansiversion=5 status=open 
  *-disk 
       description: SCSI Disk 
       product: ST3250620A 
       vendor: ATA 
       physical id: 0.1.0 
       bus info: scsi@6:0.1.0 
       logical name: /dev/sdb 
       version: 3.AA 
       serial: 5QE20QK4 
       size: 232GB 
       capabilities: partitioned partitioned:dos 
       configuration: ansiversion=5 
  *-disk 
       description: SCSI Disk 
       product: SAMSUNG HD501LJ 
       vendor: ATA 
       physical id: 0.0.0 
       bus info: scsi@0:0.0.0 
       logical name: /dev/sda 
       version: CR10 
       serial: S0MUJ1MPC10047 
       size: 465GB 
       capabilities: partitioned partitioned:dos 
       configuration: ansiversion=5 


I have tried swapping the cables, thinking that it might be trying to boot based on the SATA position, but get errors indicating that the file systems are not found, so it seems like my config is sensitive to the placement of the disks.

---

### Post by logos34 on 2008-04-13
Check that your Bios is detecting the new drive correctly.  Then make sure the new drive is listed in the hard disk boot order **last**. (I'm thinking it may be bumping your linux drive sdb from second to third position).

---

### Post by nwr222 on 2008-04-15
Thanks logos34.  It was indeed bumping my linux disk from /sdb to /sdc.  After going through recovery mode a few times I realised that it was finding everything except my /home, which lead me to the solution.
_Solution #1_
changed /dev/sdb8 in fstab to /dev/sdc8
_Solution #2_
I took a look at my fstab.  Everything except /sdb8 was using this UUID construct.  I tried using the commented last line by changing the /media/sdb8 to /home.  It did not work at first, but I worked out that it does not like the space in the options list.
My fstab now looks like:
> ...
# /dev/sdc8       /home     ext3    nodev,nosuid 0 2
UUID=8205a6d5-efcc-401e-895c-7df8e9ff4300 /home ext3 nodev,nosuid 0 2

both of these lines work (with my current cable configuration)

---

### Post by logos34 on 2008-04-15
Glad it's working now.  

The only other thing you might consider is cleaning up fstab and making a new mount point 'sd**c**5' for the ntfs partition just for the sake of consistency.

sudo mkdir /media/sdc5

Mark thread as 'solved'.

---

