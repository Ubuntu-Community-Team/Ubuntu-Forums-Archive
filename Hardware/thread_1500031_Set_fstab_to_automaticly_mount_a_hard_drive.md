---
title: "Set fstab to automaticly mount a hard drive"
date: 2010-06-02
forum: Hardware
---

### Post by mozartripper on 2010-06-02
**First run _sudo gedit /etc/fstab_ or _gksudo gedit /etc/fstab_ then enter your password you should see something like this.**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=15ba45ca-e02d-4a1f-acb8-a0bfa62abaf1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2a0629bd-ead6-40f4-a87b-3dea083ea91e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


**Now you have to create a line for your hard drive or take the one i did and adjust it to match your system**. :)

**This is an example of how to do the line see the field definitions below .**
(file System)                  (mount Point)        (partition type)  (options)     (dump)   (pass)

/dev/(sda,sdb... + Partition Number )       /media/(Drive Name)       (ntfs,ext3...)               (rw,suid...)     (0,1,2)       (0,1,2)

**In my case.**
/dev/sda5     /media/9E9A9DC99A9D9DF9   ntfs    rw,suid,dev,exec,auto,async     0     0

[U][B]
Field definitions[/B][/U]    Sources: **_[COLOR=Black]http://wiki.archlinux.org/index.php/Fstab[/COLOR]_**

    *  <file systems> - defines the storage device (i.e. /dev/sda1).

    * <mount Point> - tells the mount command where it should mount the <file system> to.

    * <partition type> - defines the file system type of the device or partition to be mounted. Many different file systems are supported. Some examples are: ext2, ext3, reiserfs, xfs, jfs, smbfs, iso9660, vfat, ntfs, swap, and auto.             The 'auto' type lets the mount command to attempt to guess what type of file system is used, this is useful for removable devices such as cdroms and dvds.

    * <options> - define particular options for filesystems. Some options relate only to the filesystem itself. Some of the more common options are: 
        * auto - File system will mount automatically at boot, or when the command 'mount -a' is issued.
        * noauto - The filesystem is mounted only when you tell it to.
        * exec - Allow the execution binaries that are on that partition (default).
        * noexec - Do not allow binaries to be executed on the filesystem.
        * ro - Mount the filesystem read only
        * rw - Mount the filesystem read-write
        * sync - I/O should be done synchronously
        * async - I/O should be done asynchronously
        * flush - specific option for FAT to flush data more often, thus making copy dialogs or progress bars to stays up until things are on the disk
        * user - Permit any user to mount the filesystem (implies noexec,nosuid,nodev unless overridden.)
        * nouser - Only allow root to mount the filesystem. (default)
        * defaults - Default mount settings (equivalent to rw,suid,dev,exec,auto,nouser,async).
        * suid - Allow the operation of suid, and sgid bits. They are mostly used to allow users on a computer system to execute binary executables with temporarily elevated privileges in order to perform a specific task.
        * nosuid - Block the operation of suid, and sgid bits.
        * noatime - Do not update inode access times on the filesystem. Can help performance (see atime options).
        * nodiratime - Do not update directory inode access times on the filesystem. Can help performance (see atime options).
        * relatime - Update inode access times relative to modify or change time. Access time is only updated if the previous access time was earlier than the current modify or change time. (Similar to noatime, but doesn't break mutt             or other applications that need to know if a file has been read since the last time it was modified.) Can help performance (see atime options). 

    * <dump> - Is used by the dump utility to decide when to make a backup. When installed (not installed by a standard installation of Arch Linux), dump checks the entry and uses the number to decide if a file system should be backed             up. Possible entries are 0 and 1. If 0, dump will ignore the file system, if 1, dump will make a backup. Most users will not have dump installed, so they should put 0 for the <dump> entry.
    
    * <pass> fsck reads the <pass> number and determines in which order the file systems should be checked. Possible entries are 0, 1, and 2. The root file system should have the highest priority, 1, all other file systems you want to             have checked should get a 2. File systems with a <pass> value 0 will not be checked by the fsck utility. 


**Once it's done run  gksudo nautilus  and add a folder with the name of the drive in /media  for me it's /media/9E9A9DC99A9D9DF9 **

**now reboot and your hard drive should be mounted every time you start your computer. :D**


Ps: 1st sry for spelling mistakes english is not my first language.
2nd this is my first post so i would like to know if what i did is good beacauz i'm new to linux thx :P

---

### Post by Jerubaal on 2010-06-08
Very handy - I need to sort mine out sometime or other!

I have a feeling that mounting to /media means the filesystem will be shown on the desktop, but mounting to /mnt won't be shown on the desktop. I'm not sure what the (dis)advantages are of either.

Also, the folder in /media or wherever needs to be created via the terminal before rebooting. Does this also need 'chmod' if it is a separate drive? As I said, I have not had the chance to sort mine out, so I have not had to deal with chmodding yet. Especially as my 'new' drive seems broken :(

---

### Post by karmila on 2010-09-20
Hi, thanks for the tip.

I have a question. I tried to automount my ntfs partition by adding this line at /etc/fstab

> LABEL=Programs /media/Programs ntfs rw,suid,dev,exec,auto,async 0 0

But then each time i deleted a file from that partition it saids "Can't move file to trash, file will be deleted immediately".

How should i write the options so deleted file won't deleted immediately  but move first to the trash, makes me can restore the files when i  change my mind.

Thanks

---

### Post by karmila on 2010-09-20
> **uulover3074 said:**
> wow, its hard to me. Never encountered this prob

Which problem?

---

