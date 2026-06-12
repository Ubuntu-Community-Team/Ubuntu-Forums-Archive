---
title: "extra drives don't mount"
date: 2008-10-14
forum: Hardware
---

### Post by noogs on 2008-10-14
Ok so I have 5 drives that I keep connected to my computer all the time. One is / another is the swap another is an external drive and the two others are extra internal drives. The problem is although the two extra internal drives are listed in the fstab by uuid they do not mount and when I try to enter one of them after boot it says I am not allowed to mount them or something (I don't remember the exact wording).
Here is my fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
#UUID=a478889b-8293-4ba5-9dae-80133e58807e /               ext3    
UUID=63d8536d-ca49-41c3-8c9a-5998890cce0a /               ext3
relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=89ef1d6d-e576-485e-870f-4a783eaceb9a none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sda1
UUID=3CC8CDF6C8CDAF08 /media/vista	ntfs(3.1)
#/dev/sdb1
UUID=C46042F76042EFAA /media/network\ drive	ntfs(3.1)
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0
```

---

### Post by Patb on 2008-10-14
Noogs, with all your drives connected as normal, open a terminal and post the output of these commands:
```
sudo fdisk -l
sudo mount -a
```
This should give some useful information which may enable someone to help.  

Cheers, Pat.

---

### Post by noogs on 2008-10-15
```
max@max-PC:~$ sudo fdisk -l
[sudo] password for max: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8899a3ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14661   117760000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           14662       30279   125451585   83  Linux
/dev/sda3           30280       30401      979965   82  Linux swap / Solaris

Disk /dev/sdb: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1228     9863878+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)

```

```
max@max-PC:~$ sudo mount -a
mount: mount point 0 does not exist
mount: mount point /media/network\ does not exist

```

---

### Post by Patb on 2008-10-15
Sorry Noogs, could you also post the output of 
```
sudo blkid
```
Cheers, Pat.

---

### Post by noogs on 2008-10-15
```
max@max-PC:~$ sudo blkid
[sudo] password for max: 
/dev/sda1: UUID="3CC8CDF6C8CDAF08" TYPE="ntfs" 
/dev/sdb1: UUID="C46042F76042EFAA" TYPE="ntfs" 
/dev/sdc1: LABEL="EXTERNAL" UUID="548F-33D6" TYPE="vfat" 
/dev/sda2: UUID="63d8536d-ca49-41c3-8c9a-5998890cce0a" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="89ef1d6d-e576-485e-870f-4a783eaceb9a" 

```

---

### Post by Yellow Pasque on 2008-10-15
First, make sure you have the ntfs-3g driver installed
```
sudo apt-get install ntfs-3g
```

It looks like you have a typo with the \ on this line:
> UUID=C46042F76042EFAA /media/network\ drive	ntfs(3.1)

Also, I've never seen an ntfs drive mounted like that. I'm used to seeing:
```
UUID=..  /mount/path   ntfs-3g  defaults  0  0
```

You might want to try ntfs-config:
```
sudo apt-get install ntfs-config
```

EDIT: Here's a handy reference for configuring ntfs-3g drives: [http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support)

---

### Post by Patb on 2008-10-15
Thanks, Noogs.  It all seems quite fixable. The first steps are to back up your fstab, make a directory to mount your second drive (and let's avoid spaces in file names here) and then to edit your fstab: 
```
sudo cp /etc/fstab /etc/fstab.bk1
sudo mkdir /media/sdb1
sudo gedit /etc/fstab
``` 
Now replace the whole of your fstab file with this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
### Note: in your post, the following line had a hard return in the middle. 
UUID=63d8536d-ca49-41c3-8c9a-5998890cce0a   /   ext3   relatime,errors=remount-ro   0   1
#   /dev/sda3
UUID=89ef1d6d-e576-485e-870f-4a783eaceb9a   none   swap   sw   0   0
/dev/scd2   /media/cdrom0   udf,iso9660   user,noauto,exec,utf8   0   0
/dev/scd0   /media/cdrom1   udf,iso9660   user,noauto,exec,utf8   0   0
/dev/scd1   /media/cdrom2   udf,iso9660   user,noauto,exec,utf8   0   0
/dev/fd0   /media/floppy0   auto   rw,user,noauto,exec,utf8   0   0
#/dev/sda1
### Note: This is a direct take from https://help.ubuntu.com/community/Fstab
/dev/sda1   /media/vista   ntfs-3g   defaults,locale=en_US.utf8   0   0
#/dev/sdb1
### Note: Let's mount your second drive at /media/sdb1/
/dev/sdb1   /media/sdb1   ntfs-3g   defaults,locale=en_US.utf8   0   0
## usbfs is the USB group in fstab file:
none   /proc/bus/usb   usbfs   devgid=126,devmode=664   0   0
```
You can delete each of the lines beginning "### Note:". They are just for your benefit. 

If this does not work for any reason, you can always use a live CD to restore your back up of /etc/fstab.  

And for everything you ever wanted to know about fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) ;)

Let us know how you go. 

Cheers, Pat.

---

### Post by noogs on 2008-10-15
ok that may have fixed it from not mounting at start up I haven't rebooted to check yet. But whenever I try to unmount or mount either drive through nautilus it says I am not privileged to do so even though I am in the root group.

---

### Post by Patb on 2008-10-15
Okay Noogs.  Let us know how it goes after you reboot.  If it's not mounted automatically or anything, please post the errors you get from:
```
sudo mount -a
```
Cheers, Pat.

---

### Post by noogs on 2008-10-15
Ok thank you the drives now mount at boot but I still am unable to unmount or remount the drives through nautilus. It's not such a big deal since this is easily done through the terminal but I was hoping to be able to do it through nautilus. No errors are shown when I run "sudo mount -a" if it helps in any way.

---

### Post by Yellow Pasque on 2008-10-15
Change the mount options of your ntfs drives in /etc/fstab from "defaults" to "users". Make sure ntfs-3g is setuid root:
```
sudo chmod u+s ntfs-3g
```

From: [http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support)

---

### Post by noogs on 2008-10-16
I changed the options to users but when i try to run "sudo chmod u+s ntfs-3g" it displays this error.
```
max@max-PC:~$ sudo chmod u+s ntfs-3g
chmod: cannot access `ntfs-3g': No such file or directory

```
I can now unmount my drives through nautilus but am still unable to remount them but there is a new error when i try to mount them.
```
Unprivileged user can not mount NTFS block devices using the external FUSE library. 
Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make 
it setuid root. Please see more information at http://ntfs-3g.org/support.html#unprivileged.
```

---

### Post by Yellow Pasque on 2008-10-16
Sorry, should have been more specific, although I'm not sure this will help if Ubuntu built their ntfs-3g without integrated fuse (sigh):
```
cd /bin
sudo chmod u+s ntfs-3g
```

---

### Post by noogs on 2008-10-16
Nope that didn't do it either but there is a new error message.
```
Mount is denied because setuid and setgid root ntfs-3g is insecure with the external 
FUSE library. Either remove the setuid/setgid bit from the binary or rebuild NTFS-3G with 
integrated FUSE support and make it setuid root.
```

---

