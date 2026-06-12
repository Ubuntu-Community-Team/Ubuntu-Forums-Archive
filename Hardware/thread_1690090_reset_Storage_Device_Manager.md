---
title: "reset Storage Device Manager"
date: 2011-02-17
forum: Hardware
---

### Post by sandman3838 on 2011-02-17
Hello

My issue is with my SDD1 hard drive.
Its just a NTFS HD that I keep extra files on.

In "Storage Device Manager" under the Dynamic Configuration Rules" I accidentally selected both "Name is SDD1" under conditions while "Specify a device file name" ARCHIVE, was also selected.  I now have a conflict going on and I can't re-enter Storage Device Manager for the SDD1 HD.  Take a look at the screen shot.

Is there something that I can run in perhaps Terminal to refresh the thing and start over?

Thank you

---

### Post by jerrrys on 2011-02-19
if this hdd just needs to be renamed try 'disk utility'

---

### Post by sandman3838 on 2011-02-19
Back again.....

Although it is mounting and I can access the files I know I'm getting some conflict from something that i have done in Storage Device Manager.

Check out this line (below) from the Command MOUNT:
/dev/ARCHIVE on /media/ARCHIVE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

I think my problem may be with PYSDM Storage device manager.  I can only run it from the ROOT and if I try and run it from my desktop I get this:

keivn@kj-desktop:~$ pysdm
/home/keivn/.themes/LK_OSX_Blue_V3/gtk-2.0/gtkrc:465: Unable to locate image file in pixmap_path: "Buttons/button-default.png"
/home/keivn/.themes/LK_OSX_Blue_V3/gtk-2.0/gtkrc:470: Background image options specified without filename
/home/keivn/.themes/LK_OSX_Blue_V3/gtk-2.0/gtkrc:1905: Unable to locate image file in pixmap_path: "Buttons/button-default.png"
/home/keivn/.themes/LK_OSX_Blue_V3/gtk-2.0/gtkrc:1908: Background image options specified without filename
keivn@kj-desktop:~$ ^C

************ MORE INFO *******************  


keivn@kj-desktop:~$ mount



keivn@kj-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/keivn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=keivn)
/dev/ARCHIVE on /media/ARCHIVE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
keivn@kj-desktop:~$ 



****************************************

keivn@kj-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda1 :
UUID=195b3699-caa4-454d-b439-9b61459a90e9	/	ext4	defaults	0	1
#Entry for /dev/sdd1 :
UUID=1E18A84F18A8282B	/media/ARCHIVE	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda5 :
UUID=1ed53506-6d3e-4736-8a26-70407d2770b1	swap	swap	sw	0	0


keivn@kj-desktop:~$ 



***************************************  



keivn@kj-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d586f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d7d0d7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sdb2           15201       30401   122102032+   f  W95 Ext'd (LBA)
/dev/sdb5           15201       30401   122102001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66305c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cc3f337

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24321   195358401    7  HPFS/NTFS
keivn@kj-desktop:~$ 



*************************************



keivn@kj-desktop:~$ sudo blkid
/dev/sda1: UUID="195b3699-caa4-454d-b439-9b61459a90e9" TYPE="ext4" 
/dev/sda5: UUID="1ed53506-6d3e-4736-8a26-70407d2770b1" TYPE="swap" 
/dev/sdb1: LABEL="WIN_XP" UUID="50600787600772D0" TYPE="ntfs" 
/dev/sdb5: LABEL="WIN_7" UUID="496C05A527BA4582" TYPE="ntfs" 
/dev/sdc1: LABEL="GAMES" UUID="01C724C13F7D1AC0" TYPE="ntfs" 
/dev/sdd1: LABEL="ARCHIVE" UUID="1E18A84F18A8282B" TYPE="ntfs" 
keivn@kj-desktop:~$

************************************ 
Finally perhaps if could help I have added a screen-shot of what another program "Disk Utility" is saying.

---

### Post by drs305 on 2011-02-21
When I try to start *pysdm* as a normal user, I am immediately prompted to run it as root and cannot get any further. I use the menu but can also start it normally with "gksu pysdm".

The setting you have in fstab for an NTFS partition should work.

I haven't seen a mount command produce a "/dev/LABEL" listing. You could open Gparted (System, Administration, Gparted) and try removing the label from there (highlight the partition, then Partition > Label).  

Or you can use Disk Utility as suggested by *jerrys* to remove or restore a label (System, Administration, Disk Utility). Highlight the partition, then "Edit Partition".

---

### Post by sandman3838 on 2011-02-21
Thanks you the info. I had used Gparted long ago I had forgotten all about it.  I installed and edited the Label.  Is seems to be working just fine.  Again thank you all for your help.

---

