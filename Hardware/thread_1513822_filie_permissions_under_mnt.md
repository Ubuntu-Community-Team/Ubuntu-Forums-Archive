---
title: "filie permissions under /mnt"
date: 2010-06-20
forum: Hardware
---

### Post by mmanjrekar on 2010-06-20
hi,

under /mnt i have created 2 directories using sudo i.e wolverine and pyre. these files initially belonged to user and group "root". with sudo chgrp i changed the group to be admin and gave file permission as 775 with sudo chmod. but when i mount any file system on these directories .... the group change to root and file permissions to 755. after i umount the drive, it changes to what i had set. 

any clues .... ?

---

### Post by IcarusR on 2010-06-20
Shouldn't create directories under /mnt for this reason.
Create mount point under /home/username & you will not have permission issues.
Of course anything mounted here will need to be mounted manually or via fstab.

---

### Post by mmanjrekar on 2010-06-21
that does seem to be a sensible workaround but not a resolution. 

i am a newbie but i believe /mnt is meant for mounting drives. and if i want to share drives with other users i would rather have them under /mnt then my home drive.

---

### Post by dino99 on 2010-06-21
install and use mountmanager (system admin mountmanager) to deal with partitions and devices rights

---

### Post by IcarusR on 2010-06-21
> that does seem to be a sensible workaround but not a resolution. 

No, that is the correct way to do it on a linux system, for security reasons. The idea is that no user has access to any thing but his home directory, which originally would be on separate partition. Thus minimising scope for fiddling & system screwups ! 
But as linux has moved into the 'home' arena it has moved away from this.

Are these drives internal or external ??

If external ubuntu should automatically mount them to a mount point of /mnt/drive label 
My ext usb drive's label is Median so it is mounted on /mnt/Median & called Median on the desktop icon as well as in Nautilus & have user read/write perms.

If they are internal then there should be a line in /etc/fstab for them both with fs type perms & mount point. 
If you are going to share them then they will need to always be mounted otherwise someone may try to access when not mounted.

---

### Post by mmanjrekar on 2010-06-21
these are internal drives .... actually my hard disk ... the logic of everything should be in home drive is true but if i want to mount something in /mnt that should be possible though ...
i have made an entry in /etc/fstab about these drives but i don't know how to set permissions there ... could you please guide me ?

---

### Post by mmanjrekar on 2010-06-21
it works under /media but not under /mnt ... if i understand correctly /mnt was the old path where devices were mounted

---

### Post by Morbius1 on 2010-06-21
All of my internal non-system partitions are either mounted to /mnt or off "/" directly so that I don't have all these icons on my desktop. It's possible that you got the process in reverse. **First **you mount them **then** you alter permissions or ownership.

You can't change the permissions on a linux file system in fstab ( that's not quite true but let's not complicate things here ) . You can only do that on windows filesystems.

---

### Post by IcarusR on 2010-06-21
Yes you are correct about /media & /mnt I was wrong.


Check the mount manpage for options 
```
man mount
```

In fstab one can set user with uid=username & group with gid=group this will determine 'ownership' of mounted drive & files. This is how I got correct perms on my networked external drive when mounted on my laptop.
My fstab line looks like this..

```
//192.168.1.50/temp          /home/andy/pad     smbfs  _netdev,credentials=/root/.smbcredentials,uid=andy,gid=andy,nounix, 0 0
```

The credentials= contains user & pw details. _netdev prevents network drives mounting till network is up. nounix is used inorder to preserve date & time stamp.

Hope this all helps.

---

### Post by Morbius1 on 2010-06-21
I didn't realize we were mounting a remote samba share. Did I miss something in the original post?

---

### Post by Morbius1 on 2010-06-21
In the event that we're not talking about a remote samba share:

Create a mount point:
```
sudo mkdir /mnt/wolverine
```Add an entry into your fstab:
( and BTW I have been assuming here all this time that we're talking about a linux filesystem , i.e., ext3 or ext4 )
```
UUID=f7927995-b098-42be-ada0-987857f5177a /mnt/wolverine           ext3    defaults        0       2
```Mount the partition:
```
sudo mount -a
```Change permissions and or ownership:
```
sudo chown morbius:plugdev /mnt/wolverine
sudo chmod 0775 /mnt/wolverine
```> In fstab one can set user with uid=username & group with gid=group  this will determine 'ownership' of mounted drive & files.  For a windows filesystem or a remote share. Not for a linux filesystem.

---

### Post by IcarusR on 2010-06-21
Morbius1

No OP is not talking about remote samba share. I was just using it as an example.

> [QUOTE]
In fstab one can set user with uid=username & group with gid=group this will determine 'ownership' of mounted drive & files.
For a windows filesystem or a remote share. Not for a linux filesystem.
[/QUOTE]

Strange as without uid & gid my linux file ownership goes haywire.

---

### Post by Morbius1 on 2010-06-22
I really hate to make absolute statements in a forum because I'm really not as smart as I've deluded myself into thinking I am but ......

uid and gid can only be used for windows filesystems: vfat or ntfs
Or for cifs ( or in your case smbfs ) as they are a filysystem in their own right and follow their own rules.
uid and gid cannot be used for linux filesystems because they store the file permissions within the filesystem itself unlike vfat and ntfs. That's why chmod or chown works on an ext3 type and not on an ntfs type.

If you attempt to use uid in fstab for a linux filesystem, for example:
>  /dev/sdb1 /mnt/wolverine ext3    defaults,uid=1000        0       2And run a sudo mount -a

You will get the following error message:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or sodmesg | tail yields:
>  EXT3-fs: Unrecognized mount option "uid=1000" or missing valueWith all due respect I believe you are confusing the mounting of a remote share, which might be on an ext3 filesystem perhaps, using smbfs ( which can use uid ) with mounting a local ext3 partition ( which cannot use uid ).

---

### Post by mmanjrekar on 2010-06-22
the problem is ...  after i mount the partition i am not able to change group or file permissions ....
.... not even with a root account.

and by the way its a vfat partition.

earlier when i used CentOS i did not face such an issues ... changing OS should ideally not change the basic logic.

and my entry in /etc/fstab appears as:

/dev/sda1     /mnt/wolverine  vfat   defaults   0   0

---

### Post by Morbius1 on 2010-06-22
>  and by the way its a vfat partition.Ah, why didn't you say so :p

Change this:
>  /dev/sda1     /mnt/wolverine  vfat   defaults   0   0     to this:
> /dev/sda1 /mnt/wolverine vfat defaults,umask=007,gid=46 0 0**umask=007** will give read / write permissions to owner ( which is root ) and group and no permissions to anyone else.
**gid=46** is the group id and it's set to "46" which represents plugdev". All local login users are members of the plugdev group.

So this will mount sda1 to /mnt/wolverine with read /write access to all local login users.

Save fstab, sudo umount /mnt/wolverine, and issue a :
```
sudo mount -a
```And you'll know instantly if I'm full of hooey.

[COLOR=Blue]EDIT: you can play around with the umask and gid to your own needs:[/COLOR]

For example umask=002 will allow read/write to user and group and read only to everyone else

A "1" turns off execute
A "2" turns off write
A "4" turns off read
And they're additive. i.e, 7 (=1+2+4) turns off everything.

[COLOR=Blue]EDIT2:[/COLOR] And it won't matter how you chown'd the original mountpoint. vfat and ntfs don't understand chown or chmod. Linux and Windows fiesystems play by different rules.

---

