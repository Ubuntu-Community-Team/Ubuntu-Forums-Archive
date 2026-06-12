---
title: "cannot mount volume hard drive"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by aj61779 on 2007-11-04
I just erased windows from my hard drive and installed linux on it.  I have a second hard drive that I use for storage.  When I try to open it it says cannot mount volume.  When I click on the details it says "$LogFile indicates unclean shutdown (0, 0) Failed to mount 'dev/hdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose on action:  Choice 1: If you have Windows then disconnect the external devices clicking ont eh 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows (I don't have Windows).  Choice 2:  If you don't have Windows then you use the 'force' option for your own responsibility.  For example type ont he command line:  mount -t ntfs-3g/dev/hdb1/media/Bree -o force Or add the option to the relevant row in the /etc/fstab file:  /dev/hdb1/media/Bree ntfs-3g defaults,force 0 0."  I've tried this and nothing happens.  I looked through the forums and found something I tried and here's what happened:
aj@aj-desktop:~$ mount ntfs-3g/dev/hdb1/media/Bree -o force
mount: only root can do that
aj@aj-desktop:~$ sudo mount ntfs-3g/dev/hdb1/media/Bree -o force
[sudo] password for aj:
mount: can't find ntfs-3g/dev/hdb1/media/Bree in /etc/fstab or /etc/mtab
aj@aj-desktop:~$ '

HELP please

---

### Post by mikewhatever on 2007-11-05
Try this
> sudo mount -t ntfs-3g /dev/hdb1 /media/Bree -o force

---

### Post by YMS_1975 on 2007-11-05
I've got the exact same message. Only my hard drive name, of course, was changed.

I typed in "sudo mount -t ntfs-3g /dev/hdb1/media/**Yousaf's Terabyte External Drive** -o force"
then exited the terminal application and nothing happened.

Any ideas on what I'm doing wrong? Could it be because of the spacing between the characters of my external hard drive name? Should it be truncated? 

All I want is to be able to access my info. on my external drive and _not lose it_  :)

I would appreciate any help.

Thanks!

---

### Post by aj61779 on 2007-11-05
Mike 
That didn't work and here's the message I get:
aj@aj-desktop:~$ sudo mount -t ntfs-3g/dev/hdb1/media/Bree -o force
[sudo] password for aj:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
aj@aj-desktop:~$ 
when I click on the harddrive Bree to open it it still says cannot mount volume and the message under details is the same

---

### Post by white3454 on 2007-11-05
A couple weeks ago I upgraded to Gutsy Gibbon and now I am unable to mount the external HDD's I have via USB.  I keep getting an error win the logfile about an improper unmount in Windows or the NTFS.
 
I'm not sure if this is an issue with Gibbon, but I did not have this issue with Fiesty... Anyway this is how I solved the problem, again it is a manual fix but it's working...  Also I do not know the consequence of doing a 'forced' mount over time, so use at your own risk....

First run the following command

sudo fdisk -l

This will give you the info you need to run the command, such as the disk location, in my case I have /dev/sdb1.

You will also need to install NTFS support, this will install the auto-config script...  this actually is not working for me like the instructions I found.

sudo apt-get install ntfs-config

now attach your drive and run the following command to force mount your drive.

 mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Good Luck!

---

### Post by aj61779 on 2007-11-05
That didn't work either got the same message in the terminal and the same message under Details when says cannot mount volume

---

### Post by aj61779 on 2007-11-05
forgot to post:
aj@aj-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x460d460d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sda: 521 MB, 521666560 bytes
32 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x76d95fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         995      509423+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 31, 32) logical=(994, 31, 31)
aj@aj-desktop:~$

---

### Post by mikewhatever on 2007-11-05
> **aj61779 said:**
> Mike 
That didn't work and here's the message I get:
aj@aj-desktop:~$ sudo mount -t ntfs-3g/dev/hdb1/media/Bree -o force...

There should be a space between nifs-3g and /dev/hdb1 and another space between /dev/hdb1 and /media/Bree. Here it is:
> sudo mount -t ntfs-3g /dev/hdb1 /media/Bree -o force

The directory /media/Bree must exist prior to that command. If it's not there, create it first with 
> sudo mkdir /media/Bree

Can you also post the output of fdisk -l.

---

### Post by aj61779 on 2007-11-05
What do I do now?
aj@aj-desktop:~$ sudo mount -t ntfs-3g /dev/hdb1 /media/Bree -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Bree: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Bree)
aj@aj-desktop:~$ sudo mount -t ntfs-3g /dev/hdb1 /media/Bree -o force
fuse: failed to access mountpoint /media/Bree: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Bree)
aj@aj-desktop:~$

---

### Post by aj61779 on 2007-11-05
sorry missed the second part of that
did this:
aj@aj-desktop:~$ sudo mkdir /media/Bree
aj@aj-desktop:~$ sudo mkdir/media/Bree
sudo: mkdir/media/Bree: command not found
aj@aj-desktop:~$ sudo mkdir /media/Bree
mkdir: cannot create directory `/media/Bree': File exists
aj@aj-desktop:~$ sudo mount -t ntfs-3g /dev/hdb1 /media/Bree -o force
aj@aj-desktop:~$ 

I can open it now thanks a lot!!!!!

---

### Post by mummra1 on 2007-11-05
white3474 on your external hard drive, do a right click, and uncheck the box 'mount as user'.  Then mount the hard drive through the GUI.  Worked great for me...best of luck.

---

### Post by vanadium on 2007-11-05
Your ntfs volume is damaged. the "-o force" option allows to mount and read it anyway. You should not, however, leave the situation as it is. You should repair the partition.

An ntfs partition can be repaired only by MS Windows. If you are a Linux only user, your best bet would be to convert the disk to ext3. This would require you to read the data from the disk to another drive, reformat the disk and then copy/move the data back to the disk.

If you do continue to read/write on the damaged ntfs partition, it will at one point become corrupt beyond repair.

---

### Post by aj61779 on 2007-11-05
can you give me step by step instructions on how to format the hard drive when using Linux only?  I don't see an option to format drive when right clicking on the hard drive and so am not sure how to do this.  Thanks

---

### Post by YMS_1975 on 2007-11-06
Holy crap, this is so friggin' complicated. 

HELP! I've tried each of these step by step, and nothing's working.

:(

---

### Post by vanadium on 2007-11-06
1) unmount (if mounted)
2) format

For example, assuming the partition you want to reformat is /dev/sdb1:

sudo umount /dev/sdb1
sudo mkft -t ext3 /dev/sdb1

---

### Post by aj61779 on 2007-11-06
ok I've reformatted it but now I can't see it when I go to Places Computer.  I see every drive but that one

aj@aj-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x460d460d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+  83  Linux

Disk /dev/sda: 521 MB, 521666560 bytes
32 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x76d95fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         995      509423+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 31, 32) logical=(994, 31, 31)
aj@aj-desktop:~$

---

### Post by aj61779 on 2007-11-06
sorry I rebooted and now i can see it but i can't write to it.  Sidenote:  I can't write to the one that has the operating system installed on it either.  HELP
How do I fix it so it so I can write to both disks.  Also would like to change the name of the secondary drive.  Refer to 
sudo fdisk -l in above post.

---

### Post by vanadium on 2007-11-07
By default, you can not write on disks under Linux as a regular user. Only the root can write anywhere. A regular user only has permission to write to his own home directory in a default  Ubuntu installation. In order to be allowed to use the second partition, you must, as root, grant yourself, as user, permissions to do so. 

1) create a directory on the new hard drive
2) give the directory to yourself as a user
3) create a link to that directory for easy access from within your home directory (with the name of your choosing, let us assume: "data")

You did not tell the current "name " of the disk. Let us assume it is mounted in /media/sdb1

sudo mkdir /media/sdb1/data
sudo chown $USER:$USER /media/sdb1/data
sudo ln -l /media/sdb1/data ~/data

Substitute the users login for $USER. If it is for yourself, you can type $USER as is: it gets substituted by your actual user name. This creates a "directory" data that you can reach from within your home directory.

Other people will advice you to chown the mount point. It you are the sole user of the system, you can do that. The approach I propose is more flexible, though. In the same way, you can create directories for other users on that volume. The end user just needs to know the link in his home folder (with the name he wants, he can even delete and recreate it), while only the root has to be concerned over where the mount point is.

---

### Post by iGeorgie on 2007-11-07
> **white3454 said:**
> A couple weeks ago I upgraded to Gutsy Gibbon and now I am unable to mount the external HDD's I have via USB.  I keep getting an error win the logfile about an improper unmount in Windows or the NTFS.
 
I'm not sure if this is an issue with Gibbon, but I did not have this issue with Fiesty... Anyway this is how I solved the problem, again it is a manual fix but it's working...  Also I do not know the consequence of doing a 'forced' mount over time, so use at your own risk....

First run the following command

sudo fdisk -l

This will give you the info you need to run the command, such as the disk location, in my case I have /dev/sdb1.

You will also need to install NTFS support, this will install the auto-config script...  this actually is not working for me like the instructions I found.

sudo apt-get install ntfs-config

now attach your drive and run the following command to force mount your drive.

 mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Good Luck!

For me this was the solution! I still got a few error messages, but after that it worked! 
Many thanks!:)

---

### Post by aj61779 on 2007-11-07
It's showing the name of the disk in properties as 111.8 GB Volume: disk
This is what happens:
aj@aj-desktop:~$ sudo mkdir /media/hdb/111.8 GB Volume: disk
mkdir: cannot create directory `/media/hdb/111.8': No such file or directory
mkdir: cannot create directory `GB': File exists
mkdir: cannot create directory `Volume:': File exists
mkdir: cannot create directory `disk': File exists
aj@aj-desktop:~$ 
aj@aj-desktop:~$ sudo mkdir /media/hdb1/111.8 GB Volume: disk
mkdir: cannot create directory `GB': File exists
mkdir: cannot create directory `Volume:': File exists
mkdir: cannot create directory `disk': File exists
aj@aj-desktop:~$ 


aj@aj-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x460d460d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+  83  Linux

Disk /dev/sda: 521 MB, 521666560 bytes
32 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x76d95fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         995      509423+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 31, 32) logical=(994, 31, 31)
aj@aj-desktop:~$

---

### Post by aj61779 on 2007-11-07
I don't know if this will help you help me or not but here it is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2a217ec3-6e8c-40d4-b7e0-12062ce6159f /               ext3    defaults,erro$
# /dev/hda5
UUID=f1bc53c4-1754-4c45-a204-84bd7cd75513 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0








                               [ Read 11 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by vanadium on 2007-11-07
Your drive /dev/hdb1 currently is not anymore mounted. You will need to update your /etc/fstab file to change the file system options. Post the output here of 

cat /etc/fstab

and I will tell you what you need to change.

---

### Post by aj61779 on 2007-11-07
here you go
aj@aj-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2a217ec3-6e8c-40d4-b7e0-12062ce6159f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f1bc53c4-1754-4c45-a204-84bd7cd75513 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
aj@aj-desktop:~$

---

### Post by aj61779 on 2007-11-07
> **vanadium said:**
> 


Other people will advice you to chown the mount point. It you are the sole user of the system, you can do that. The approach I propose is more flexible, though. In the same way, you can create directories for other users on that volume. The end user just needs to know the link in his home folder (with the name he wants, he can even delete and recreate it), while only the root has to be concerned over where the mount point is.

Other sidenote I am the sole user of the system and don't want anyone else to be able to write to these drives if I add a user so if you can tell me how to do it this way that would be awesome.

Thanks.

---

### Post by vanadium on 2007-11-08
I should not have asked you to post /etc/fstab because you already did it before, my apologies. This thread has become very confusing, and I have been confused as well. Your fdisk -l tells that the volume is /dev/sdb1 and that it is recognized  as a Linux file system. It is not in your /etc/fstab, however. Because you accessed it before, it must be a removable drive. A removable drive in principle is mounted automatically with permissions for the user, i.e. not through fstab. I will once more need you to post some outputs, all together in one post to have an overview of your current configuration and to see wheather the drive is well mounted. It has now become too confusing to gather your details over the three pages of this thread. Otherwise, I just can continue to guess.

sudo blkid
mount
ls -l /media

This will tell me what the system sees, what is currently mounted, and what the permissions of the mount points are.

---

### Post by aj61779 on 2007-11-08
The drive is not removable it is a 2nd internal hard drive

aj@aj-desktop:~$ sudo blkid
[sudo] password for aj:
/dev/hda1: UUID="2a217ec3-6e8c-40d4-b7e0-12062ce6159f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="f1bc53c4-1754-4c45-a204-84bd7cd75513" 
/dev/hdb1: UUID="e63603de-b1c1-462c-ae89-818683b05a9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: SEC_TYPE="msdos" LABEL="LG USB Driv" UUID="3398-8BDE" TYPE="vfat" 
aj@aj-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/LG USB Driv type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
aj@aj-desktop:~$ ls -l /media
total 48
drwxr-xr-x 2 root root  4096 2007-11-05 08:20 Bree
lrwxrwxrwx 1 root root     6 2007-11-04 12:54 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 cdrom0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 cdrom1
lrwxrwxrwx 1 root root     7 2007-11-04 12:54 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 floppy0
drwxr-xr-x 4 root root  4096 2007-11-07 08:05 hdb1
drwxr-xr-x 2 root root  4096 2007-11-07 08:01 hdb111.8
drwx------ 2 aj   root 23040 1969-12-31 18:00 LG USB Driv
aj@aj-desktop:~$

---

### Post by vanadium on 2007-11-09
The partition /dev/hdb1 is "seen' by the system as an ext3 volume
However, it is not mounted.

Verify that "Mount removable drives when hot-plugged" is checked in System - Preferences - Removable drives and media. Unplug the drive and plug it back in. use the command

mount

to verify if it includes or not a line starting with /dev/hdb1. If it does, note the mount point (the second entry on the line). Then you should be able to list the drives content with the command ls <moint point> substituting the moint point (could be /media/sdb but could also be something else).

If it doesn't, then try mounting the drive manually and post error messages, if any, here.

sudo mkdir test
sudo mount /dev/hdb1 test

If there are no error messages, then we know that your external drive /dev/hdb1 can mount normally, but doesn't for one or another reason that I can't tell.

---

### Post by aj61779 on 2007-11-09
Not an external drive.  are the commands the same?

---

### Post by vanadium on 2007-11-09
Indeed, i missed you said it is an internal drive. then, it is simple: it is not in your /etc/fstab, thus not mounted automatically. You need to edit /etc/fstab and add a line for your partition. You already have a directory /media/hdb1 that can serve as mount point. To edit your /etc/fstab, load it in gedit as root user:

gksudo gedit /etc/fstab

Add the following two lines:
```

# /dev/hdb1
UUID=e63603de-b1c1-462c-ae89-818683b05a9d /media/hdb1 ext3 defaults,errors=remount-ro 0 2

```

Exit gedit, saving the file. I took the UUID from the output of your blkid command. According to your output of ls /media, there is a directory there called hdb1 that can be used as mount point.

So save you further trouble, give yourself as a user permission to do anything in the mount point:

sudo chown $USER:$USER /media/hdb1

This is different from the advice I gave before, which is more suited for a multi user system and if you understand the system a little better.

Now reload /etc/fstab

sudo mount -a

You should not have any output from this command. If there is an error, post it here. Else, your partition should be accessible with all rights for you as a user enabled.

---

### Post by aj61779 on 2007-11-10
I did this but now it says I cannot mount the volume because I do not have permission when I try to write to it.

aj@aj-desktop:~$ sudo chown $USER:$USER /media/hdb1
[sudo] password for aj:
aj@aj-desktop:~$ sudo mount -a
aj@aj-desktop:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2a217ec3-6e8c-40d4-b7e0-12062ce6159f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f1bc53c4-1754-4c45-a204-84bd7cd75513 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/hdb1
UUID=e63603de-b1c1-462c-ae89-818683b05a9d /media/hdb1 ext3 defaults,errors=remount-ro 0 2

aj@aj-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2a217ec3-6e8c-40d4-b7e0-12062ce6159f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f1bc53c4-1754-4c45-a204-84bd7cd75513 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/hdb1
UUID=e63603de-b1c1-462c-ae89-818683b05a9d /media/hdb1 ext3 defaults,errors=remount-ro 0 2
aj@aj-desktop:~$ 

aj@aj-desktop:~$ sudo blkid
/dev/hda1: UUID="2a217ec3-6e8c-40d4-b7e0-12062ce6159f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="f1bc53c4-1754-4c45-a204-84bd7cd75513" 
/dev/hdb1: UUID="e63603de-b1c1-462c-ae89-818683b05a9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: SEC_TYPE="msdos" LABEL="LG USB Driv" UUID="3398-8BDE" TYPE="vfat" 
aj@aj-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/LG USB Driv type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/hdb1 on /media/hdb1 type ext3 (rw,errors=remount-ro)
aj@aj-desktop:~$ ls -l /media
total 48
drwxr-xr-x 2 root root  4096 2007-11-05 08:20 Bree
lrwxrwxrwx 1 root root     6 2007-11-04 12:54 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 cdrom0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 cdrom1
lrwxrwxrwx 1 root root     7 2007-11-04 12:54 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2007-11-04 12:54 floppy0
drwxr-xr-x 3 root root  4096 2007-11-06 18:48 hdb1
drwxr-xr-x 2 root root  4096 2007-11-07 08:01 hdb111.8
drwx------ 2 aj   root 23040 1969-12-31 18:00 LG USB Driv
aj@aj-desktop:~$ 

aj@aj-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x460d460d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+  83  Linux

Disk /dev/sda: 521 MB, 521666560 bytes
32 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x76d95fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         995      509423+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 31, 32) logical=(994, 31, 31)
aj@aj-desktop:~$

---

### Post by aj61779 on 2007-11-10
nevermind once i restarted it all worked great.

Thanks a LOT for your help!!!!

---

### Post by aj61779 on 2007-11-10
do i do the same thing for the hda1 drive?

also, I still don't know how to change the names of the drives can you tell me how to do that?

---

### Post by The Drift Demon on 2007-11-21
**[COLOR="Red"]This is what I did.[/COLOR]**

     user@Laptop:~$* [COLOR="Blue"]sudo mount -t ntfs-3g /dev/sdc1 /media/Disk -o force[/COLOR]*
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdc1 (Disk)

Then I typed the mount all command.
     user@Laptop:~$ *[COLOR="Blue"]sudo mount -a[/COLOR]*

Then I went to the file browser and clicked on the Disk, and it worked.

---

### Post by aj61779 on 2007-12-03
so i reinstalled linux 7.10 (i needed windows for some things so created dual boot).  now i can't seem to get into the /etc/fstab.  it keeps telling me I don't have permission.  I don't understand.  Help!!!
aj@aj-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bbd1b7f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2356    18924538+   7  HPFS/NTFS
/dev/hda2   *        2357        4882    20290095   83  Linux
/dev/hda3            4883        4998      931770    5  Extended
/dev/hda5            4883        4998      931738+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x460d460d

   Device Boot      Start         End      Blocks   Id  System
aj@aj-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
aj@aj-desktop:~$ 

aj@aj-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f654c897-e081-4a64-a4e3-2305a72c16f8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=bea93737-52dc-49b7-a131-7064fdc3a05d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
aj@aj-desktop:~$

---

