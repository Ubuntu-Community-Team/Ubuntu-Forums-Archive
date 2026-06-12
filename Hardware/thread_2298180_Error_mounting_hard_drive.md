---
title: "Error mounting hard drive"
date: 2015-10-09
forum: Hardware
---

### Post by Donnie Love on 2015-10-09
My hard drive won't mount and I get this error:

```
Error mounting /dev/sda1 at /media/donnie/d1de92ab-8a08-4693-84f4-39dec381f552: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/donnie/d1de92ab-8a08-4693-84f4-39dec381f552"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Can anyone tell me what this all means? And the big question: How can I fix it?

Os: Lubuntu 14.04 LTS

---

### Post by oldfred on 2015-10-09
Is sda an internal drive?

Post this:
sudo parted -l
sudo blkid
cat /etc/fstab

---

### Post by Donnie Love on 2015-10-09
It is internal.

```

donnie@R103:~$ sudo parted -l
[sudo] password for donnie: 
Model: ATA ST3500413AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  488GB  488GB   primary   ext4            boot
 2      488GB   500GB  12.6GB  extended
 5      488GB   500GB  12.6GB  logical   linux-swap(v1)

``````

donnie@R103:~$  sudo blkid
/dev/sda1: UUID="d1de92ab-8a08-4693-84f4-39dec381f552" TYPE="ext4" 
/dev/sda5: UUID="650e97c7-e4de-4722-bebd-34c5a31adbdb" TYPE="swap" 
/dev/sdb1: UUID="2da48137-4d36-419d-9d51-5b9117ace81f" TYPE="ext4" 
/dev/sdb5: UUID="9c0c115f-30f9-44be-94ca-d6b69be0f378" TYPE="swap" 

```
There are 2 hard drives, not sure which is which here ^. sda1 is the one giving me heart attacks. sdb1 is working.

```


donnie@R103:~$  cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2da48137-4d36-419d-9d51-5b9117ace81f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9c0c115f-30f9-44be-94ca-d6b69be0f378 none            swap    sw              0       0

```

---

### Post by oldfred on 2015-10-09
You changed drive order. 
Did you plug in sda drive after install to now sdb drive. Fstab says it was sda when you installed it.
Or it could just be BIOS changed order.
Grub normally installs to drive that is sda. And system normally boots from sda, but in BIOS you can change that easily to default to sdb.

Not sure if corruption issue or just a ownership & permissions issue.

You can run fsck on your sda1 from you install, if it is not mounted.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

You also can see if you can manually  mount it before or after the e2fsck.


 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda1 /mnt/data
#where sda1 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)

But generally better if internal drive to have it mounted by fstab.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.


 fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=d1de92ab-8a08-4693-84f4-39dec381f552 /mnt/data ext4 defaults,noatime 0 2

---

### Post by Donnie Love on 2015-10-09
The drive I'm trying to access was the primary drive with Ubuntu 11.10 in it. I unplugged it and plugged in new drive to load Lubuntu 14.04, but that was before I installed it.

I think I did this right. Here's what I got:
```

donnie@R103:~$  sudo e2fsck -C0 -p -f -v /dev/sdb1
[sudo] password for donnie: 
/dev/sdb1 is mounted.
e2fsck: Cannot continue, aborting.


donnie@R103:~$  sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sdb1 is mounted.
e2fsck: Cannot continue, aborting.


donnie@R103:~$  sudo parted -l
Model: ATA ST3500413AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  488GB  488GB   primary   ext4            boot
 2      488GB   500GB  12.6GB  extended
 5      488GB   500GB  12.6GB  logical   linux-swap(v1)


Model: ATA WDC WD5000AZRX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4022MB  extended
 5      496GB   500GB  4022MB  logical   linux-swap(v1)


donnie@R103:~$  sudo mkdir /mnt/data
donnie@R103:~$  sudo mount /dev/sda5 /mnt/data
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
donnie@R103:~$  sudo chmod -R a+rwX,o-w /mnt/data
donnie@R103:~$  sudo chown -R $USER:$USER /mnt/data


```
If I didn't do it right, you may have to dumb it down for me. I'm not very technically literate. :0T

---

### Post by oldfred on 2015-10-09
You need to unmount it, as it is saying it is mounted and fsck only works on unmounted partitions.
I just posted a standard example and as it says you need to change to your partition which is sda1. 
Change all sda5's to sda1 in all examples I posted. 
If you need I can edit above to be correct, so you can copy & paste?

Sorry posted example of mount with sda5, you need to use your partition or sda1.

---

### Post by Donnie Love on 2015-10-10
> **oldfred said:**
> 
If you need I can edit above to be correct, so you can copy & paste?


If you're willing to do that, I would be most grateful. I don't really know what I'm doing.

---

### Post by oldfred on 2015-10-10
Changed examples in post above to use sda1 which it your current partition with issues. 
But double check drive order. Sometimes it changes.
sudo fdisk -lu
Or
sudo parted -l

---

### Post by Donnie Love on 2015-10-10
That definitely did something, because now I can see folders, but still can't access. Permission denied.

```
Error opening directory '/media/donnie/3ba69986-019a-497d-8f85-54538c5820dd/media/39B2-5A67': Permission denied
```

---

### Post by oldfred on 2015-10-10
Did you try the manual mount (make sure you have not mounted or tried to mount already with Nautilus).
And then give yourself ownership & permissions with chown and chmod commands posted above?

I also like to give partitions labels, so they mount with the label if not already mounted with fstab automatically with a reboot. I have lots of extra partitions and have to have the labels to know which is which. I try to remember to label when using gparted, but later will use Disks to set labels.

---

### Post by Donnie Love on 2015-10-10
**YES!!!** ...*ahem* I mean, yes, I tried it once and nothing. I tried it the second time and I'm in! Thank you so much! You just helped me recover about 15 years worth of work, about 20,000 bits of media, thousands of fonts and all my photos. They are copying now.

---

### Post by oldfred on 2015-10-10
Glad that worked.

Now best to plan a really good backup plan. Not just one copy.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by Donnie Love on 2015-10-11
I'm still having trouble with the annoying permission problem. The chmod and chown functions don't seem to be permanent. It reverts after I reboot. And even when it does work, I can't get my fonts off the old hard drive.

Edit: the problem seems to be with the new hard drive.

---

### Post by oldfred on 2015-10-11
If it is ext4 or any Linux format permissions & ownership should stay.

 But it NTFS or any Windows format the permissions & ownership are part to the mount process and cannot be changed by chown and chmod.

In Disks and the icon in upper right of Disks is Smart Status. It will tell you about drive and run tests. But all I know is passed is good and anything else is not.

---

### Post by Donnie Love on 2015-10-11
Tight security is a fine thing, but if I can't access my own files it's  too tight. I shouldn't have to beg my computer for permission to use my  own files.

I found "SMART Data & Self Tests..." under settings button. Both drives are Ext4. Neither have Windows on them. SMART is not enabled. (I enabled it - no difference)

Now what do I do?

---

### Post by oldfred on 2015-10-11
In terminal change to that partition(s) and post this:

ls -l

Like this:
fred@trusy-ar:~$ cd /mnt/data
fred@trusy-ar:/mnt/data$ ls -l
total 96
drwxrwxr-x  3 fred fred  4096 May  1 15:25 Calibre_Library
drwxrwxr-x 20 fred fred 12288 Oct  8 23:18 Documents

And if a file something like this:
-rw-rw-r--  1 fred fred     459 Dec 24  2014 hex

---

### Post by Donnie Love on 2015-10-11
[ 3 fred fred  4096 May  1 15:25 Calibre_Library ] is the name of the folder I want to access?

---

### Post by oldfred on 2015-10-11
That just happened to be my first. You want to change to the one you are having issues with.

How are you mounting it, Nautilus or manually?
From live installer or a working install?
Live installer uses user 999 where install uses user 1000 which could be an issue.

---

### Post by Donnie Love on 2015-10-12
It's [ /usr/share/fonts ] on both drives.

drwxrwxr-x /usr/share/fonts

It says command not found

---

### Post by oldfred on 2015-10-13
That shows everyone can read the directory.
You did not show ownership.
The ls command has to exist. Did you leave off the space after ls? Or not use l -el, not 1 - one, nor I- cap i.
ls -l

---

### Post by Donnie Love on 2015-10-13
```
donnie@R103:~$ drwxrwxr-x /usr/share/fonts
drwxrwxr-x: command not found
donnie@R103:~$ cd /mnt/data
donnie@R103:/mnt/data$ ls -l
total 0
donnie@R103:/mnt/data$ drwxrwxr-x /usr/share/fonts
drwxrwxr-x: command not found
donnie@R103:/mnt/data$ 

```

> 
Did you leave off the space after ls? Or not use l -el, not 1 - one, nor I- cap i.

No , to be sure I copied and pasted everything.
My guess is something comes before the [ /usr/share/fonts ], but I don't know what goes there.

---

### Post by oldfred on 2015-10-13
You may have created the mount point /mnt/data, but not mounted your data partition on sdb to it?
donnie@R103:/mnt/data$ ls -l
total 0

Shows no files or folders.

This is not a command, but should be the output of the ls -l
drwxrwxr-x /usr/share/fonts

---

### Post by Donnie Love on 2015-11-10
I still can't get access to the fonts folder...
I'm lost using this code. I don't know what any of this stuff means:
> **oldfred said:**
> 

How are you mounting it, Nautilus or manually? 
From live installer or a working install?
Live installer uses user 999 where install uses user 1000 which could be an issue.

I did get this result but don't know where to go from here:
```

donnie@R103:~$ cd /usr/share/fonts
donnie@R103:/usr/share/fonts$ ls -l
total 16
drwxr-xr-x 2 root root 4096 Aug  5 01:15 cmap
drwxr-xr-x 8 root root 4096 Aug  5 01:16 truetype
drwxr-xr-x 3 root root 4096 Aug  5 01:14 type1
drwxr-xr-x 5 root root 4096 Aug  5 01:16 X11
donnie@R103:/usr/share/fonts$ 


```
In the properties it says the content can be changed only by the owner. That's fine, but why doesn't it recognize me as the owner?

---

### Post by oldfred on 2015-11-11
System files are supposed to be owned by root. And never change that on system files or you will have to reinstall.

If you need to copy files in the system you need sudo or temporary admin rights as root.
       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by Donnie Love on 2015-11-12
OK, I've read all that (most of it). I understand the risks. I just want to drag & drop some files, not change the nature of the universe or anything like that. I entered the commands, but nothing changed. What do I do now?

---

### Post by oldfred on 2015-11-12
Dragging & dropping system files can destroy a system.

But if just a file or two that you want to copy & move you can run Nautilus with gksudo from terminal.
Be sure to immediately close that copy of Nautilus or you may accidentally move files you should not.

gksudo nautilus

Do not use sudo with GUI applications, but they are not wanting uses to even use gksudo, so it may not even be installed. If not you should still be able to install it.

The correct way is terminal command using sudo

sudo cp /path/file /path/file

see
man cp
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

---

### Post by Donnie Love on 2015-11-12
Excellent. I got my fonts back.

And I'm able to boot into the old hard drive.

Thanks again for your help. :0>

---

