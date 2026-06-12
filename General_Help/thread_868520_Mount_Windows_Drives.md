---
title: "Mount Windows Drives"
date: 2008-07-23
forum: General Help
---

### Post by th3gh05t on 2008-07-23
Hi-

I just finished installing Ubuntu 8.0.4. When I go to "Places", I can see all of my Windows XP partitions under "Removable Media".

When I click on a drive, it takes a second for the window to pop up and it creates an icon on my desktop. (I am assuming Linux is mounting the drive.)

How do I make it so it does this automatically on start up?

I have a USB external hard drive that automatically gets mounted when Ubuntu starts up and that icon appears on the desktop. So I don't see why it wouldn't work with the Windows drives.

Furthermore, how do I prevent it from creating icons on the desktop?

Thanks for your time!

---

### Post by iaculallad on 2008-07-23
> **th3gh05t said:**
> Hi-

I just finished installing Ubuntu 8.0.4. When I go to "Places", I can see all of my Windows XP partitions under "Removable Media".

When I click on a drive, it takes a second for the window to pop up and it creates an icon on my desktop. (I am assuming Linux is mounting the drive.)

How do I make it so it does this automatically on start up?

I have a USB external hard drive that automatically gets mounted when Ubuntu starts up and that icon appears on the desktop. So I don't see why it wouldn't work with the Windows drives.

Furthermore, how do I prevent it from creating icons on the desktop?

Thanks for your time!

Post whatever outputs when you issue the commands below on your terminal:

```
sudo fdisk -l
cat /etc/fstab

```

And, to prevent Drive icons from displaying on the Desktop, press Alt+F2 and input "gconf-editor" (w/o quote). Navigate to **apps->nautilus->desktop** and uncheck the value **volumes_visible**. Close the window.

---

### Post by th3gh05t on 2008-07-24
sudo fdisk -l

```
root@derek-desktop:~# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03cd5cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12078    97016503+   7  HPFS/NTFS
/dev/sda2           12079       24320    98333865    f  W95 Ext'd (LBA)
/dev/sda5           12079       24320    98333833+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedcdedcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4462    35840983+   7  HPFS/NTFS
/dev/sdb2   *        4463        8944    36001665    7  HPFS/NTFS
/dev/sdb3            8945       30401   172353352+   f  W95 Ext'd (LBA)
/dev/sdb5            8945       14701    46243071    7  HPFS/NTFS
/dev/sdb6           14702       30401   126110218+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabf18a78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x981db8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       91201   732572001    7  HPFS/NTFS

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by iaculallad on 2008-07-24
Say, it's the /dev/sda5 that needs to be auto-mounted:

First thing to do is to install ntfs-3g driver.

```
sudo apt-get install ntfs-3g
```

Then, create the mount point for that device:

```
sudo mkdir /media/NTFSDrive1
```

Open /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

and add the line of code below to the last part of the file:


/dev/sda5 /media/NTFSDrive1 ntfs-3g defaults 0 0

Save and Close the File: Drop to your terminal and issue the command:

```
sudo mount -a
```

Follow the steps with the other NTFS partition you would like to be automounted. Just create a unique mount point for each device you want included.

---

### Post by Victormd on 2008-07-24
If you're still having problems, check the link on my signature...

---

### Post by th3gh05t on 2008-07-24
Thanks for the simple steps!

Since most of my drives are already mounted on "/media/something", how do I figure out what "/dev/sda5" matches?

---

### Post by iaculallad on 2008-07-24
> **th3gh05t said:**
> Thanks for the simple steps!

Since most of my drives are already mounted on "/media/something", how do I figure out what "/dev/sda5" matches?

On your terminal:

```
sudo blkid
```

or you could simply look at your fstab file.

```
cat /etc/fstab
```

---

### Post by th3gh05t on 2008-07-24
> **iaculallad said:**
> And, to prevent Drive icons from displaying on the Desktop, press Alt+F2 and input "gconf-editor" (w/o quote). Navigate to **apps->nautilus->desktop** and uncheck the value **volumes_visible**. Close the window.

Thanks for helping me mount the drives! Your instructions worked!

I did this step before I edited fstab, but it didn't work. The icons are still on the desktop. I went back into "gconf-editor" just to make sure, and the value was unchecked.

Any other ideas?

---

### Post by th3gh05t on 2008-07-24
Anyone have any ideas on how to **not** display mounted partitions upon start up?

Thanks, Derek

---

### Post by iaculallad on 2008-07-24
> **th3gh05t said:**
> Anyone have any ideas on how to **not** display mounted partitions upon start up?

Thanks, Derek

:confused: Unchecking the volumes_visible option should prevent you're mounted drives from displaying on your Desktop.

Try to log off from your account then log back in (With the volumes_visible option unchecked).

---

### Post by th3gh05t on 2008-07-24
> **iaculallad said:**
> :confused: Unchecking the volumes_visible option should prevent you're mounted drives from displaying on your Desktop.

Try to log off from your account then log back in (With the volumes_visible option unchecked).

Hmm..

Ya, it's still not working. I have logged off, logged back on. Still there. I have rebooted, and they are still there.

If I try and delete the icon, it only asks me to "Unmount" the drive.

Really strange that option isn't working..

---

### Post by iaculallad on 2008-07-24
Though this may be similar from navigating to gconf-editor, try it using the terminal:

```
sudo gconftool-2 --type boolean -s /apps/nautilus/desktop/volumes_visible false
```

---

### Post by th3gh05t on 2008-07-24
Ya, that didn't do it either. I logged off and back on, still there. Darn it!

---

