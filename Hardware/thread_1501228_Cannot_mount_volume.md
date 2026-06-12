---
title: "Cannot mount volume"
date: 2010-06-04
forum: Hardware
---

### Post by yeravgjoe on 2010-06-04
I'm running ubuntu from a CD_ROM and am trying to mount the hard drive for my Toshiba U305.  It was running Win7, but I picked up a virus from a wi-fi connection in Monterey, CA last Saturday.  I'm hoping I'll be able to mount the drive, move my data to an external USB drive, and then install ubuntu on the Toshiba U305 laptop.

I can get ubuntu to boot from the CD_ROM, but it won't mount the volume for my system hard drive.  I've tried to force the mount using this command:

mount -t ntfs-3g /devsda2 /media/ToshibaU305 -o force

I get the error "only root can do that"

I think this means I can't force a mount unless I'm the root user.  How do I log in as the root user if I've booted up using the CD_ROM?  When I go to System > Administration > Users and Groups the only user that appears is the user named "root."

---

### Post by sites on 2010-06-04
Did you try using sudo?

**sudo** mount -t ntfs-3g /devsda2 /media/ToshibaU305 -o force

or.....

su root

or.....

sudo su

I could be imagining things, but if memory serves me correctly the livecd uses "password" as the password for root.

---

### Post by yeravgjoe on 2010-06-04
If I use this command:

sudo mount -5 ntfs-3g /dev/sda2 /media/ToshibaU305 -o force

I get this error:

fuse:  failed to access mountpoint /media/ToshibaU305:  No such file or directory

If I use this command:

mkdir /media/ToshibaU305

I get this error:

mkdir:  cannot create directory /media/ToshibaU305 : Permission denied

---

### Post by sites on 2010-06-04
With Lucid, all NTFS disks have mounted automagically for me, even in LiveCD.  With previous versions i always got a popup suggesting the "force" option.  Did you get the same popup with this drive?

Did you try using sudo before that mkdir command?

---

### Post by yeravgjoe on 2010-06-05
Thanks, that did the trick!  Now I just have to get my data off the laptop hard drive.  :)

---

