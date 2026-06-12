---
title: "Clean Install and migrate to new HD"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by emtjr928 on 2009-11-04
I have searched and can't find a specific how-to. I have an old Installation of Jaunty that has been Upgraded starting with Dapper. Originally was a dual boot with Win2k. Here is the current drive info:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6068    48741178+  83  Linux
/dev/sdb2   *        6069       14593    68477062+   f  W95 Ext'd (LBA)
/dev/sdb5            6069        8601    20346291   83  Linux
/dev/sdb6            8602        8729     1028128+  82  Linux swap / Solaris
/dev/sdb7            8730       14593    47102548+  83  Linux

I have installed a new Hard drive since I'm starting to have concerns about the old one. Here is it's info:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

What I want to accomplish is a clean install on the NEW 320gb drive, Move my data, email, bookmarks/settings etc.to the new drive. I envision partitioning the new drive:

1- swap
2- /     primary
3- /home primary
4- /data extended

I want to wind up with a cleaner install, all my data and settings, I know I may have to reinstall some programs and the vmware that I have to run the occaisional windows app.

Any point in the right direction will be appreciated.
Thanks, Ed

---

### Post by jjcv on 2009-11-04
It looks to me like you are heading in the right direction.  Install ubuntu in the way you suggest:

1- / primary
2- swap
3- /home primary
4- /data extended

Once the install has finished then you can mount your old drive:

sudo mount /dev/sdb3  /mnt (or /dev/sdb7 - where ever your old home directory was on).

The copy all your old files over.  ie

cd /mnt/[oldhomedir]   so you are inside your old homedir

find . -print | cpio -pdmua /home/[newhomedir]

All your files will be copied over.

Reboot.

You can do the same with your VMWare images if you know where they are on the old system.  In /var/lib/vmware usually I think.

---

### Post by emtjr928 on 2009-11-05
Well everything has gone good to a point. BUT, I have one partition that I can't access even though it appears to be mounted.1,2 and 3 are fine but can't access sda4 or 5.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         128     1028128+  82  Linux swap / Solaris
/dev/sda2   *         129        3167    24410767+  83  Linux
/dev/sda3            3168        9246    48829567+  83  Linux
/dev/sda4            9247       38913   238300177+   5  Extended
/dev/sda5            9247       38913   238300146   83  Linux


here is fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8bbebad0-604a-4deb-8ba1-dce8930c1c64 /               ext3    errors=remount-ro 0       1
# /data was on /dev/sda5 during installation
UUID=cc44cb9d-e067-4536-a42f-8fb66e3d9f44 /data           ext3    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=1da3a997-b387-427e-a64c-e3c1fcfd563f /home           ext3    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=9fd4679b-6ba0-468d-8455-3fcc2a652f3e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


AND:

emtjr928@emtjr928-desktop:~$ sudo blkid
/dev/sda1: UUID="9fd4679b-6ba0-468d-8455-3fcc2a652f3e" TYPE="swap" 
/dev/sda2: UUID="8bbebad0-604a-4deb-8ba1-dce8930c1c64" TYPE="ext3" 
/dev/sda3: UUID="1da3a997-b387-427e-a64c-e3c1fcfd563f" TYPE="ext3" 
/dev/sda5: UUID="cc44cb9d-e067-4536-a42f-8fb66e3d9f44" TYPE="ext3" 


Does sda4 have to mounted as well?

---

### Post by jjcv on 2009-11-05
You should be able to mount /dev/sda5, well it should automount as it is in your /etc/fstab.

have you created /data for it to mount onto?

sudo mkdir /data
sudo mount /data

Forget sda4, it is simply the whole extended partion where sda5 is the actual file system under it.

---

### Post by emtjr928 on 2009-11-05
Did some more poking around. It looks like the partition is showing up as a sub-folder named "data" under the file system tree. I was looking for it as a separate item in the nautilus tree. ie. Home Folder, File System, Data. Which is really how I would like it to be.

---

