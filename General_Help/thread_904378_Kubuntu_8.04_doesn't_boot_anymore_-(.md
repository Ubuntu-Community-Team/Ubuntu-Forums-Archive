---
title: "Kubuntu 8.04 doesn't boot anymore :-("
date: 2008-08-29
forum: General Help
---

### Post by claus on 2008-08-29
Hi,

after trying to fix what I perceived as errors in /etc/fstab, Kubuntu dosn't boot anymore. :-( I am writing this message using the live system of Ubuntu 5.10). Is it possible to access my installation somehow via the live system and fix fstab? (I made a backup of the old fstab, but it is stored in my /home partition - /dev/hda8 -, which I cannot access.)

The reason why I edited fstab is, that after a failed installation of the NVIDIA graphics driver (my graphics card is an old RIVA TNT 2 64), Kubuntu doesn't work properly anymore, and there were some "cryptic" strings inside fstab, which I found strange. When booting, I got the message 'FILE SYSTEM IS NOT CLEAN'. (All attempts to burn a new image on a CD failed because of errors of some kind. (I have to use a Windows system to download and burn the image, which has no md5sum checking ability.)

I'm reall hoping that someone can give me a hint on how to solve this problem.

TIA,

Claus

---

### Post by kagashe on 2008-08-29
Use mount command to see whether hda8 is already mounted or not:
> $ mount
If you don't see that hda8 is mounted proceed as follows:
> $ sudo mkdir /media/hda8
$ sudo mount /dev/hda8 /media/hda8

Now you can browse /media/hda8/home/username

and locate the file.

Mount the partition where Kubuntu is located by the same method say it is hdax
Replace /etc/fstab
> $ sudo cp backupfilename.txt /media/hdax/etc/fstab

kagashe

---

### Post by Zeroangel on 2008-08-29
Yep, definitely. You'll first want to find out what partition your ubuntu root folder is on (ie: hda1). Then you should be able to use the command line to mount it, and then fix the fstab that way. Like so:
```
su
mkdir /media/ubuntu-home
mkdir /media/ubuntu
mount -t ext3 /dev/hda8 /media/ubuntu-home
mount -t ext3 /dev/hda1 /media/ubuntu
```That would be assuming that your main ubuntu partition is located on /dev/hda1

Then if you want, open 2 instances of "gksudo nautilus", and use that to do the renaming and copying of the files.

Adjust it to fit your needs.

---

### Post by claus on 2008-08-29
Hi,

thanks to your suggestions I am now able to access both the '/' and '/home' partition. Here's the "weird" fstab I tried to fix. Is this "normal" for 8.04? At least to me it looks kinda weird:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5f0d02d6-4d00-4452-b2ac-1c2a70ff0663 /               reiserfs relatime        0       1
# /dev/sda1
UUID=e504c713-9881-4ce7-8221-f2797f1eb6ad /boot           reiserfs notail,relatime 0       2
# /dev/sda8
UUID=70860176-1bb3-4e2c-bb41-7cf72dc9ab3d /home           reiserfs relatime        0       2
# /dev/sda7
UUID=9a81c576-00df-4913-95b7-7a5d75aec03e /usr            reiserfs relatime        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Shouldn't it read '/dev/hda5' and so forth? And 'relatime' looks strange     to me, either. The entry by which I tried to replace this (i. e. '/dev/sda5') goes as follows:

/dev/hda5   /  reiserfs defaults   0   2

What would be properly here?

Claus

---

### Post by caljohnsmith on 2008-08-29
> **claus said:**
> Hi,

thanks to your suggestions I am now able to access both the '/' and '/home' partition. Here's the "weird" fstab I tried to fix. Is this "normal" for 8.04? At least to me it looks kinda weird:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
[COLOR="Red"]UUID=5f0d02d6-4d00-4452-b2ac-1c2a70ff0663 /               reiserfs relatime        0       1[/COLOR]
# /dev/sda1
UUID=e504c713-9881-4ce7-8221-f2797f1eb6ad /boot           reiserfs notail,relatime 0       2
# /dev/sda8
UUID=70860176-1bb3-4e2c-bb41-7cf72dc9ab3d /home           reiserfs relatime        0       2
# /dev/sda7
UUID=9a81c576-00df-4913-95b7-7a5d75aec03e /usr            reiserfs relatime        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Shouldn't it read '/dev/hda5' and so forth? And 'relatime' looks strange     to me, either. The entry by which I tried to replace this (i. e. '/dev/sda5') goes as follows:
[COLOR="Red"]
/dev/hda5   /  reiserfs defaults   0   2[/COLOR]

What would be properly here?

Claus
One problem is that "/dev/hda5" doesn't exist on your machine, since it is actually called "/dev/sda5". :) If you use:
```
sudo blkid
```
I think you will see that the UUID of sda5 is the same as you have above in your fstab, namely "5f0d02d6-4d00-4452-b2ac-1c2a70ff0663". The UUID is just a different way of designating the partition, and it has some advantages over just using the device name /dev/sda5. The main advantage of UUIDs is if you move your HDD around, e.g change it from master to slave, or maybe put it in another slot, then the UUIDs will still be consistent, whereas the device name will change from /dev/sda5 to maybe /dev/sdb5 for instance. 

So bottom line is, even though the fstab entries may look "strange", I think your fstab entry for sda5 is probably fine the way it is. If you want more info on fstab and UUIDs and such, see the [ubuntu.com page on fstab]("https://help.ubuntu.com/community/Fstab"). :)

---

