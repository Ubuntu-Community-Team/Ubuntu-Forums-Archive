---
title: "External USB drive permissions"
date: 2005-11-28
forum: General Help
---

### Post by auroraborealis on 2005-11-28
I've search the forum, but couldn't find a solution.

When Ubuntu auto-mounts an external device (i.e. my USB harddrive), the permissions are set so that the owner has 'rwx', but no one else has any access. Even with 'sudo chmod 766' or similar commands the permissions don't change. I've even messed around with /etc/mtab with no avail.

What can I do so that other users/groups can have read/execute access to /media/<device>?

---

### Post by HighPlainsDrifter on 2005-11-30
[QUOTE=auroraborealis]I've search the forum, but couldn't find a solution.

When Ubuntu auto-mounts an external device (i.e. my USB harddrive), the permissions are set so that the owner has 'rwx', but no one else has any access. Even with 'sudo chmod 766' or similar commands the permissions don't change. I've even messed around with /etc/mtab with no avail.

What can I do so that other users/groups can have read/execute access to /media/<device>?[/QUOTE]

Mtab only shows a list of currently mounted filesystems.

There are about a million threads related to your issue...

[http://www.ubuntuforums.org/showthread.php?t=87862&highlight=usb+mount+permission](http://www.ubuntuforums.org/showthread.php?t=87862&highlight=usb+mount+permission)
[http://www.ubuntuforums.org/showthread.php?t=88531&highlight=usb+mount+permission](http://www.ubuntuforums.org/showthread.php?t=88531&highlight=usb+mount+permission)
[http://www.ubuntuforums.org/showthread.php?t=39561&highlight=automount+usb+permissions](http://www.ubuntuforums.org/showthread.php?t=39561&highlight=automount+usb+permissions)

Check those out. In short, it seems people recommend using chmod on the appropriate /media/<whatever>.

---

### Post by RAOF on 2005-11-30
It actually depends upon the filesystem on the external drive.  If it's a linux filesystem (ie: one which supports postix file permissions, like ext2/3, reiserfs, xfs, etc) you should be able to just "sudo chown" various directories under its mount point.

If it has a non-linux filesystem (like FAT32, NTFS, etc), they don't actually support file permissions (well, NTFS does, but there's no linux support for that).  So chown, chmod, etc won't actually have any effect - they will silently fail, I believe.  In this case you'll need to make sure that the drive is mounted with different mount paramaters (namely something like fmask=0111,dmask=0000 (taken from the [ubuntu wiki]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windowspartition%29")).  I think this will require some udev black magic, but I don't really have any idea how to do it.

---

### Post by auroraborealis on 2005-12-01
Thanks for the suggestions. I manually added an entry to /etc/fstab and now it works.

---

### Post by towsonu2003 on 2005-12-01
[QUOTE=auroraborealis]Thanks for the suggestions. I manually added an entry to /etc/fstab and now it works.[/QUOTE]

could you post the output of your fstab pls? thanks (have same issue, my editing of fstab did not work -> maybe yours will?)

---

### Post by RAOF on 2005-12-01
[QUOTE=auroraborealis]Thanks for the suggestions. I manually added an entry to /etc/fstab and now it works.[/QUOTE]
Ok, yeah.  That'll also work ;)  But you should be careful if you plug in another usb storage device - it might confuse things.

---

### Post by auroraborealis on 2005-12-13
[QUOTE=towsonu2003]could you post the output of your fstab pls? thanks (have same issue, my editing of fstab did not work -> maybe yours will?)[/QUOTE]

```
$ cat /etc/mtab
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/EXT vfat rw,noexec,nosuid,nodev,umask=0022,user=username 0 0
``````

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                   0     0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0     1
/dev/hdc        /media/cdrom0   udf,iso9660 user,unhide,noauto     0     0
/dev/sda1       /media/EXT      vfat    user,rw,umask=0022         0     0

```
Edit: Notice the /dev/sda1 on mtab and fstab match up.

---

### Post by auroraborealis on 2005-12-13
[QUOTE=RAOF]Ok, yeah.  That'll also work ;)  But you should be careful if you plug in another usb storage device - it might confuse things.[/QUOTE] Yes, whenever I plug another USB drive in it, crazy things do happen. BUT doing another cat /etc/mtab and finding the exact /dev/sd[a-c]1 and putting that NEW [a-c] into /etc/fstab works. It's not elegant, but it works.

---

### Post by soulestream on 2005-12-13
couldnt you just edit udev rules so it gives everyone access?

soule

---

### Post by auroraborealis on 2005-12-13
How would I go about this?

I changed the MODE in this line of permission.rules

BUS=="scsi", KERNEL=="sd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k 'usb ieee1394'", RESULT="1", MODE="0640", GROUP="plugdev"

to 0744, but it doesn't work.

---

