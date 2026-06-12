---
title: "NTFS Drive not displayed in Xubuntu"
date: 2008-05-20
forum: Hardware
---

### Post by Harmonix444 on 2008-05-20
I am currently trying to figure out what is going out with my 2nd hard drive. I previously had Ubuntu installed on my computer, but someone suggested I run Xubuntu because I have a older system. When I had Ubuntu, my 2nd drive was displayed. Now that I have installed Xubuntu, I cannot even see where the drive is located. 

Here's the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=86fb78c3-57a6-4032-809b-5872303c3027 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3d017bc6-c61f-4e3e-96db-b5c7d2a50b6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by nicedude on 2008-05-20
Your fstab file is a list of what drives will be mounted at boot time and your mtab file in the same directory as fstab is the list of currently mounted disks. So in general you need to run a mount command or use a mount utility to get the NTFS partition to mount and then open mtab and note the bottom line that should reflect this partition then add that line to your fstab file so that it will be repeated at boottime. this should correct your problem. In your fstab example I see no NTFS partitions listed currently so I am sure that is it.

nicedude

---

### Post by peitschie on 2008-05-20
You need to do several things to find the partition if it isn't automatically mounted.

First, you need to find the partition
```

sudo fdisk -l | grep NTFS

```
To explain this, fdisk -l displays all the disk partitions (so if you run this without the 'grep' part it will show all partitions').  'grep' just restricts the output so only lines with NTFS (hopefully the missing partition) will be listed.

If you get more than one partition listed, you will need to figure out which one/s you want to mount.

Once you find the drive, you need to create a directory in /media to mount this partition to... e.g:
```
sudo mkdir /media/ntfs_drive
```

Then you can mount the drive using the following command
```
sudo mount /dev/[device found in the fdisk step, e.g., sda1] /media/ntfs_drive
```

If all goes well this should get you up and running.  You can find out more options for the mount command by doing ```
man mount
``` from a terminal.

---

### Post by Harmonix444 on 2008-05-20
> **peitschie said:**
> You need to do several things to find the partition if it isn't automatically mounted.

First, you need to find the partition
```

sudo fdisk -l | grep NTFS

```
To explain this, fdisk -l displays all the disk partitions (so if you run this without the 'grep' part it will show all partitions').  'grep' just restricts the output so only lines with NTFS (hopefully the missing partition) will be listed.

If you get more than one partition listed, you will need to figure out which one/s you want to mount.

Once you find the drive, you need to create a directory in /media to mount this partition to... e.g:
```
sudo mkdir /media/ntfs_drive
```

Then you can mount the drive using the following command
```
sudo mount /dev/[device found in the fdisk step, e.g., sda1] /media/ntfs_drive
```

If all goes well this should get you up and running.  You can find out more options for the mount command by doing ```
man mount
``` from a terminal.

I was able to find the NTFS drive, but tried following the other steps, and said that it was not able to do it...

Am I supposed to put everything that I get back from the fdisk? 
I've tried that, and nothing has happened. I still have not been able to mount the drive or anything...


Thanks for all your help... Any other suggestions?

---

### Post by peitschie on 2008-05-20
What error messages do you get?  It might be that the /media directory doesn't exist.  

You may also not have ntfs-3g installed.  To install ntfs-3g do the following in a terminal:
```

sudo apt-get install ntfs-3g

```

The only part you need from fdisk is the '/dev/sd??' part, which is what you plug into the mount command to tell it which device is the ntfs partition.  Again, what errors do you get returned from the commands?

---

### Post by Harmonix444 on 2008-05-20
> **Harmonix444 said:**
> I was able to find the NTFS drive, but tried following the other steps, and said that it was not able to do it...

Am I supposed to put everything that I get back from the fdisk? 
I've tried that, and nothing has happened. I still have not been able to mount the drive or anything...


Thanks for all your help... Any other suggestions?

/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
**ntfs partition...

harmonix@Harmonix:~$ sudo mount /dev/sdb1/media/ntfs_drive
mount: can't find /dev/sdb1/media/ntfs_drive in /etc/fstab or /etc/mtab

---

### Post by peitschie on 2008-05-20
You missed a space ;).  It should be "sudo mount /dev/sdb1 /media/ntfs_drive" (note the space after /dev/sdb1)

---

### Post by Harmonix444 on 2008-05-20
> **peitschie said:**
> You missed a space ;).  It should be "sudo mount /dev/sdb1 /media/ntfs_drive" (note the space after /dev/sdb1)

Once I do that... should it display something?

---

### Post by peitschie on 2008-05-20
Nope.  It will just return to the command line without any errors.  You can verify that /dev/sdb1 has mounted by running
```

mount

```

The last line listed (or listed somewhere) should be /dev/sdb1.  Now, the way we have done this won't automatically remount after a reboot.  Once this has all workd and you can access the drive properly though I will post the next steps to make this boot on start up automatically :-)

---

### Post by Harmonix444 on 2008-05-20
> **peitschie said:**
> Nope.  It will just return to the command line without any errors.  You can verify that /dev/sdb1 has mounted by running
```

mount

```

The last line listed (or listed somewhere) should be /dev/sdb1.  Now, the way we have done this won't automatically remount after a reboot.  Once this has all workd and you can access the drive properly though I will post the next steps to make this boot on start up automatically :-)

When I put "mount":
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by Harmonix444 on 2008-05-20
> **Harmonix444 said:**
> When I put "mount":
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

I got it to work!!!

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/ntfs_drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by peitschie on 2008-05-20
Well done :)

The next question is are you able to write to the drive?  To access the files, open a file manager to /media/ntfs_drive.  You may not be able to write, because we'll need to do a few extra things...

Firstly, check the output of typing the following in a terminal
```
groups
```
You *should* be a member of plugdev (hopefully).  If you aren't, you can add yourself by typing the following and then LOGGING OFF AND ON AGAIN
```
sudo adduser <your username> plugdev
```

Next, we need to get the group id of plugdev.  This can be done by running 
```
grep plugdev /etc/group
```
You need to remember (or write down) the 2-3 digit number just after the second ":" (e.g., mine is 46)
Then we can remount the drive with the appropriate permissions so that you can drive
```

sudo umount /media/ntfs_drive # Unmount the existing partition
sudo mount -o  defaults,umask=007,gid=<group id found before> /dev/sd?? /media/ntfs_drive

```
To explain this, the umask instructs the mount command to make the directory group-writeable, while the gid instructs the mount command to mount with the specified group-id (in this case we want plugdev).

Once this is done you need to test creating a file on the ntfs partition again to check that this has all worked properly.

---

### Post by twist2b on 2008-05-20
that happens to me sometimes. This happens when I forget to turn off my windows partition correctly. Like i just turn off manually. try going onto windows and turn it off correctly, should work.

---

### Post by dprestemon on 2008-05-20
I just stumbled across this while starting to research a different problem.  I am using Hardy, but had a second hard drive with Windows that had files I needed.  It would not mount.  I was getting the error message "Your system does not support NTFS."  Followed your directions to Harmonix and voila, life is good.  Thanks a million, peitschie!

---

### Post by peitschie on 2008-05-20
twist2b... that would be the case if the drive wasn't automatically mounting ;-).  In this case however, I don't believe Xubuntu does automounting the same way Ubuntu does, so the issue is getting the drive to mount in the first place.

You are correct though that either hibernating windows, or an incorrect shutdown will mark the NTFS partition as dirty and require a chkdsk to be run under windows...

Glad you found the instructions useful dprestemon :)

---

### Post by Harmonix444 on 2008-05-20
> **peitschie said:**
> Well done :)

The next question is are you able to write to the drive?  To access the files, open a file manager to /media/ntfs_drive.  You may not be able to write, because we'll need to do a few extra things...

Firstly, check the output of typing the following in a terminal
```
groups
```
You *should* be a member of plugdev (hopefully).  If you aren't, you can add yourself by typing the following and then LOGGING OFF AND ON AGAIN
```
sudo adduser <your username> plugdev
```

Next, we need to get the group id of plugdev.  This can be done by running 
```
grep plugdev /etc/group
```
You need to remember (or write down) the 2-3 digit number just after the second ":" (e.g., mine is 46)
Then we can remount the drive with the appropriate permissions so that you can drive
```

sudo umount /media/ntfs_drive # Unmount the existing partition
sudo mount -o  defaults,umask=007,gid=<group id found before>

```
To explain this, the umask instructs the mount command to make the directory group-writeable, while the gid instructs the mount command to mount with the specified group-id (in this case we want plugdev).

Once this is done you need to test creating a file on the ntfs partition again to check that this has all worked properly.

The last command is not working properly it seems. it just gives me details on how the 'mount' command works...

---

### Post by jma79 on 2008-12-16
Hi there

I was having the same problem with xubuntu and ntfs partitions and was able to solve it with peitschie's instructions. So thanx for that! :)
However one thing that's missing is what is needed to do so that when booting the partitions would be automounted?

Thx in advance.

---

### Post by peitschie on 2008-12-16
Hi jma79,

To get this to automount you need to add the appropriate line in /etc/fstab.

Open fstab in an editor by running the following in a gnome-terminal:
```
gksu gedit /etc/fstab
```

To the end of the file, you need to add a line similar to the following:
```
/dev/sda1 /media/storage  ntfs    defaults,umask=007,uid=1000,gid=46 0       1
```
This will mount the /dev/sda1 device to the /media/storage directory (which must already exist prior to running this command).  Make sure you set an appropriate user id (uid) and group id (gid) so that you can write to the drive.

Then save that, and reboot to make sure it works!

---

### Post by peitschie on 2008-12-16
Harmonix444,

I just realised I never chased up your last problem.  That final line should have read:
```
sudo mount -o  defaults,umask=007,gid=<group id found before> /dev/sd?? /media/ntfs_drive
```

Whups!

---

