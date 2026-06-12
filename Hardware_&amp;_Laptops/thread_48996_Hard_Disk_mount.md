---
title: "Hard Disk mount?"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by D-Vine on 2005-07-14
So i've got 6 partititions on this disk and i've got 2 other HD's connected
how can i show'm in "Computer"? like mount them or something like that
ty

---

### Post by varunus on 2005-07-14
You need to add the partitions to /etc/fstab.  First, go to a terminal and type "sudo gedit /etc/fstab"

Mine looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0        0

```

The last line was added by me  :) 

To add more filesystems, just follow the above format.  The ubuntuguide ([www.ubuntuguide.org](www.ubuntuguide.org)) has some pointers on how to use it.  Generally, you can add filesystems the following way:

/dev/hda*    /empty/mountpoint   auto   defaults,user   0   0

Make sure to make an empty folder to use as the mountpoint.  The command "fdisk -l" can list your partitions.

---

### Post by D-Vine on 2005-07-14
hmmm tnx, but euhm the ubuntu site?:p lol, tried it already, don't understand a thing what's on it:p first time linux user, you know :oops:

---

### Post by Lunde on 2005-07-14
[QUOTE=D-Vine]hmmm tnx, but euhm the ubuntu site?:p lol, tried it already, don't understand a thing what's on it:p first time linux user, you know :oops:[/QUOTE]
 Give me a list of the partitions you want to mount and just paste your fstab here and I'll type it up for you.

Open a terminal window and type:
**gedit /etc/fstab**
Paste the output of the file here..

Then give me a list of your partitions
Ex: 
hda1 = ntfs -- (Partition info: your windows partition)
hda5 = fat32 -- (Partition info: your shared partition)

---

### Post by D-Vine on 2005-07-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda8       /tmp            ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


i've look up everything with the sudo fdisk -l thingie, this i what i got

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1240     9960268+  83  Linux
/dev/sda2            1241       24792   189181440    5  Extended
/dev/sda5            1241        5950    37833043+  83  Linux
/dev/sda6            5951       10660    37833043+  83  Linux
/dev/sda7           10661       16313    45407691   83  Linux
/dev/sda8           16314       24792    68107536   83  Linux

==> these are all NTFS disks, only the first partitition is used by linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

==> this is my windows disk, also NTFS

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         608     4883728+   b  W95 FAT32
/dev/hdb2             609        1825     9775552+   f  W95 Ext'd (LBA)
/dev/hdb5             609        1221     4923891    b  W95 FAT32
/dev/hdb6            1222        1825     4851598+   b  W95 FAT32

==> this is a HD with just some files on it, FAT32

hope this is enough for you?
ow yeah, euhm, mounting them wouldn't do something like formatting them, would it? :-?

---

### Post by Lunde on 2005-07-15
These are the lines I added to your fstab, note that your NTFS is read only. There are utilities that can allow you to RW but if you don't have to I don't recommend it.

/dev/sdb1 /mnt/sdb1_ntfs        ntfs     ro,dmask=0222,fmask=0333   0 0
/dev/hdb1 /mnt/hdb1_fat32     vfat user,rw,exec 0 0
/dev/hdb5 /mnt/hdb5_fat32     vfat user,rw,exec 0 0
/dev/hdb6 /mnt/hdb6_fat32     vfat user,rw,exec 0 0

**So here's what you do (Without the $ in th commands):**

Creating a backup of your fstab:
**$ sudo cp /etc/fstab /etc/fstab.backup**

Making the mount directories:
**$ sudo mkdir /mnt/sdb1_ntfs /mnt/hdb1_fat32 /mnt/hdb5_fat32 /mnt/hdb6_fat32**

Edit the fstab:
**$ sudo gedit /etc/fstab**

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /home ext3 defaults 0 2
/dev/sda8 /tmp ext3 defaults 0 2
/dev/sda6 /usr ext3 defaults 0 2
/dev/sda7 /var ext3 defaults 0 2
#----------------------------------------------------------* Your new drives
/dev/sdb1 /mnt/sdb1_ntfs  ntfs     ro,dmask=0222,fmask=0333   0 0
/dev/hdb1 /mnt/hdb1_fat32     vfat user,rw,exec 0 0
/dev/hdb5 /mnt/hdb5_fat32     vfat user,rw,exec 0 0
/dev/hdb6 /mnt/hdb6_fat32     vfat user,rw,exec 0 0
#----------------------------------------------------------* End 
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```

**Save and exit!**

Mounting your drives:
**$ sudo mount -a**

You now have 4 new directories under /mnt/ where you can access your drives

**NOTE:** If you get any errors, post them here after you restore your backup:
**$ mv /etc/fstab.backup /etc/fstab**

---

### Post by Lunde on 2005-07-15
These are the lines I added to your fstab, note that your NTFS is read only. There are utilities that can allow you to RW but if you don't have to I don't recommend it.

/dev/sdb1 /mnt/sdb1_ntfs        ntfs     ro,dmask=0222,fmask=0333   0 0
/dev/hdb1 /mnt/hdb1_fat32     vfat user,rw,exec 0 0
/dev/hdb5 /mnt/hdb5_fat32     vfat user,rw,exec 0 0
/dev/hdb6 /mnt/hdb6_fat32     vfat user,rw,exec 0 0

**So here's what you do (Without the $ in th commands):**

Creating a backup of your fstab:
**$ sudo cp /etc/fstab /etc/fstab.backup**

Making the mount directories:
**$ sudo mkdir /mnt/sdb1_ntfs /mnt/hdb1_fat32 /mnt/hdb5_fat32 /mnt/hdb6_fat32**

Edit the fstab:
**$ sudo gedit /etc/fstab**

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /home ext3 defaults 0 2
/dev/sda8 /tmp ext3 defaults 0 2
/dev/sda6 /usr ext3 defaults 0 2
/dev/sda7 /var ext3 defaults 0 2
#----------------------------------------------------------* Your new drives
/dev/sdb1 /mnt/sdb1_ntfs  ntfs     ro,dmask=0222,fmask=0333   0 0
/dev/hdb1 /mnt/hdb1_fat32     vfat user,rw,exec 0 0
/dev/hdb5 /mnt/hdb5_fat32     vfat user,rw,exec 0 0
/dev/hdb6 /mnt/hdb6_fat32     vfat user,rw,exec 0 0
#----------------------------------------------------------* End 
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```

**Save and exit!**

Mounting your drives:
**$ sudo mount -a**

You now have 4 new directories under /mnt/ where you can access your drives

**NOTE:** If you get any errors, post them here after you restore your backup:
**$ mv /etc/fstab.backup /etc/fstab**

---

### Post by D-Vine on 2005-07-16
Tnx, it did the trick

---

### Post by Lunde on 2005-07-16
there's also a possibuility to mount the drives under your **/home/username** if you find that more  convenient.

You can do this by changing the mount directory in fstab:
change the: **/mnt/hdXX_XXX** to **/home/username/hdXX_XXX **where **X** = dirs I named for you and **username** = your own username(do not use "**~/**"

Then in terminal as your own user (**Without sudo**):
**$ mkdir ~/sdb1_ntfs ~/hdb1_fat32 ~/hdb5_fat32 ~/hdb6_fat32**

Then you can delete the old mount points under /mnt/

---

### Post by wh0rd on 2005-08-14
Okay this is the thing i've had the fstab as:

/dev/hda5       /media/x  vfat    iocharset=utf8,umask=000   0       0

then all was fine i was able to read write but now it's a different story. now whatever i do to the fstab it doesn't allow me to read or write to the /mnt/x mount. I have no idea why, hope you can shed some light on this.

---

### Post by wh0rd on 2005-08-15
I tried mounting it in a different place /media/windows and it works, but then the problem arises again whenever I open Limewire and use a folder in that mount to share it on Limewire! Could this be some sort of security feature of the firewall??? I installed Firestarter,,,

---

