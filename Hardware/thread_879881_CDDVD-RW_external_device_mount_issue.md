---
title: "CD/DVD-RW external device mount issue"
date: 2008-08-04
forum: Hardware
---

### Post by petrofski on 2008-08-04
Hi everyone,

I've recently installed Ubunto in my laptop and although I'm familiar with Unix I'm totally new to this.

I have an external CD/DVD-RW device which I would like to read/write from...

I've tried zillions combinations of manual mountings and as well the auto.
All fail with 1 of the following errors:

Mount: no medium found
AND
Mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


if I type in 'mount' it lists

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/petrofski/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=petrofski)

> cat etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3460a766-5c79-4baa-bfd6-0a6ad18b1a84 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=67963428-28b4-4a91-8d16-0ece8e9c6078 none            swap    sw              0       0
**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0**
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I though linux would just mount and appear on desktop a path to the filesystem... but doesn't o.O

Plz!!! Help!!!

---

### Post by mc4man on 2008-08-04
Why don't you hook up the drive, put some media of a known type like a dvd movie or audio cd or a data cd/dvd _not created_ on vista and run
> sudo lshw -C disk

The ext. cd/dvd drive should be scdx, in your case probably /dev/scd1
In addition to above you could run this in a maximized terminal to see if it's listed.
> cat /etc/udev/rules.d/70-persistent-cd.rules

---

### Post by petrofski on 2008-08-04
Thanks for the quick reply. The problem was yet in something totally unthinkable: the external driver I'm using is an old dell I have... which RW speed is maxed (or even unique) at 24x... as the data CDs I was trying to read were written at much higher then that.
I guess that was it cause I burned another data CD at 24x and it worked o.O

---

