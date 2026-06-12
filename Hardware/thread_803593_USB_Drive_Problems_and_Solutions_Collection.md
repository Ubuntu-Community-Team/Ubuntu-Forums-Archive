---
title: "USB Drive Problems and Solutions Collection"
date: 2008-05-22
forum: Hardware
---

### Post by jbulcher on 2008-05-22
[COLOR="Sienna"]I've been having some trouble getting Ubuntu to recognize an acomdata usb hard drive, so I was searching through the forums trying to find a solution to the problem. I noticed that there were a significant number of threads devoted to finding solutions solving similar problems with usb drives. In the interest of finding a solution myself, and also to help other people find solutions, can all of you out there post any unique problems you've encountered working with usb drives and hard drives, and the solution you came up with?

Please, only list problems with solutions.[/COLOR]

Here's something to get the thread started. I know it's not as on-topic as I would like for the rest of the thread, but it's a start:

I mounted a fat32 partition using ```
sudo mount -t msdos /dev/sdX1 /mnt/usb
``` but I was unable to copy any files onto it that had spaces in the name. I also couldn't change any permissions (obviously) so that the entire drive was accessible only as root. Since the program that needed to access the drive used a unique group for access to the files it needs, I discovered that fat32 was completely inappropriate for use with the current setup with the program.

Solution: use a different file system.

---

### Post by xender69 on 2008-06-18
Hi,
I'm having a similar problem.  I have an external USB drive and in the /etc/fstab I put:
/dev/sdg1 /media/usbdrive vfat defaults 0 1

and when I execute mount -a it works but as a normal user, I can't edit/add/delete anything off this drive.  As root, I tried to give the permission of 777 and while the command works, when I look at the filesystem, it shows back up as 755.

Help please.

Thanks in advance.

---

### Post by jbulcher on 2008-06-21
Hi xender69

The problem is because the fat32 file format doesn't store permissions. Therefore, you can't change any permissions on files and folders on the drive. I'm sure there's a way to mount the drive with a different set of permissions; try 'man mount'. Otherwise, the drive will only be accessible as administrator.

---

### Post by lswb on 2008-06-21
The msdos type partition is like an old pre-windows 95 partition. It does not support filenames with spaces or names loner than the old 8.3 name length. Change it from msdos to vfat and it will support the same file names as Windows 95/98/ME/NT/XP etc.

Also Jbulcher, you are correct, access to a vfat partition for non-root users can be made by the entry for that partition in /etc/fstab. In particular the 4th field of the fstab entries. As you suggested, check out man page for mount command for details you can do a web search for a howto for more info.

---

### Post by dark_phantom on 2008-06-21
> **xender69 said:**
> Hi,
I'm having a similar problem.  I have an external USB drive and in the /etc/fstab I put:
/dev/sdg1 /media/usbdrive vfat defaults 0 1

and when I execute mount -a it works but as a normal user, I can't edit/add/delete anything off this drive.  As root, I tried to give the permission of 777 and while the command works, when I look at the filesystem, it shows back up as 755.

Help please.

Thanks in advance.

You need to specify to write/read on the fstab.  Do a mount | grep usbdrive and it will show read-only.

/dev/sdg1 /media/usbdrive vfat -rw defaults 0 1

---

