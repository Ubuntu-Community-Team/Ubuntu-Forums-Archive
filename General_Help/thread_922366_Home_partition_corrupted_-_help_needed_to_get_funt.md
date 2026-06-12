---
title: "Home partition corrupted - help needed to get funtional system"
date: 2008-09-17
forum: General Help
---

### Post by jenkinbr on 2008-09-17
I lost my /home partition on Monday, possibly due to an application I tried installing via WINE.  My music immediately stopped, and all of my wallpapers were lost.  I have a backup that I made using Parted Magic, but unfortunatly, I was unable to restore it because I didn't burn all of the image files to DVD properly (I am missing images 8 and 32).

When I rebooted to Ubuntu, It dropped to a root terminal because it could not find /dev/sda2 (my /home partition).  A quick look at windows' disk management utility revieled that the partition no longer existed.

I had restored what I could to my home partition after using gparted to reformat it.  When I rebooted Ubuntu, I got the same error that I did before, and was brought to a root terminal.

My first course of action was to get a listing of /dev/disk/by-uuid:
```

16904ADE904AC3C9
75471d97-5af2-4bb2-9ed9-54f9be2727ba
7883-EFAB
8e097c49-b7e9-49a3-bbe5-e7a123aac4bd
f783369b-09a6-47ae-bce9-09d2399b1b11

```
I wrote all of these UUIDs down and compared them to what was in /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=75471d97-5af2-4bb2-9ed9-54f9be2727ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=8e097c49-b7e9-49a3-bbe5-e7a123aac4bd /home           ext3    relatime        0       2
# /dev/sda1
UUID=16904ADE904AC3C9 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=f783369b-09a6-47ae-bce9-09d2399b1b11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
As you can see, all the UUIDs match up with each other, except for 7883-EFAB, which is my flash drive, which I mounted to store my /etc/fstab on.

Now I have no idea what the problem is.  Mounting /dev/sda2 to /home worked fine, I typed 'exit' and was brought to the login prompt for ubuntu.  I logged in as usual, and gnome spit out a ton of errors.  Does this mean that I need to start over, or is there something else I can do to get my system relatively closer to where it was in my backup image?

---

### Post by vanadium on 2008-09-17
It is unlikely for a partition to disappear, and you showed that indeed it has not disappeared.

From your explanation, I learn thet it goes wrong as soon as you are longing in. This can indicate that files in your home directory indeed are missing, not accessible or otherwise corrupt.

The very first thing I would do now is try to saveguard my personal user data if you did not do so already. Preferably you would start a live session of Ubuntu, mount the partition containing your home and copy your user documents, etc. to a safe location.

I am not sure for the rest: you say you can mount your home partition fine. During startup, it is checked. There is no indication that the file system is damaged.

What you can try first is to create a different account. If that goes fine, then surely the issue is in missing configuration files in your standard account. The easiest remedy of restoring your system probably will be to remove that account, delete the home directory and recreate the account.

Do not worry to much about your system as such. Ubuntu is free and can be reinstalled in less than 45 minutes. It is your personal data that you need to worry about. The time spend to make an image of a partition is better spend making a copy of your user data. With a synchronisation utility such as rsync, you can update a backup copy in seconds.

---

### Post by jenkinbr on 2008-09-17
Thanks for your reply.  I will give that a try regarding creating a new user account, recreating the old one, and then restoring my files.  As for the /home partition, it was actually wiped out completely.  What I have now is all of the files that were in the first 4GB of backups.  I made a mistake when I burned those backups to disk, and the software that I used did not like that.

Most of my data as of 2008-08-03 is intact, and I have a good backup of everything dated sometime in June.

---

