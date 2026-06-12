---
title: "can't find /dev/cdrom in /etc/fstab or /etc/mtab"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by lynn derricks on 2009-07-15
After upgrading to jaunty the CD-ROM is not detected

**fstab info:**
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=053a9b79-f25b-4996-8f64-e9b49a55c5bb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=030a6b8a-090a-496e-87cd-6226bdd40dc1 none            swap    sw              0       0
/dev/scd0 /media/cdrom1udf,iso9660 user,noauto,exec,utf8 0       0

**[COLOR=black]Receive the following errors [/COLOR]**
derrick@derrick-desktop:~$ sudo mount /dev/scd0
[sudo] password for derrick: 
mount: special device /dev/scd0 does not exist
derrick@derrick-desktop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/derrick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=derrick)

derrick@derrick-desktop:~$ sudo mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab
derrick@derrick-desktop:~$ sudo mount /dev/scd1
mount: can't find /dev/scd1 in /etc/fstab or /etc/mtab
derrick@derrick-desktop:~$ sudo mount /dvd
mount: can't find /dvd in /etc/fstab or /etc/mtab

lynn derricks

---

### Post by kilowattradio on 2009-07-15
> **lynn derricks said:**
> After upgrading to jaunty the CD-ROM is not detected
derrick@derrick-desktop:~$ sudo mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab
derrick@derrick-desktop:~$ sudo mount /dev/scd1
mount: can't find /dev/scd1 in /etc/fstab or /etc/mtab
derrick@derrick-desktop:~$ sudo mount /dvd
mount: can't find /dvd in /etc/fstab or /etc/mtab

lynn derricks

```

man mount
sudo mount /media/cdrom
sudo mount -t iso9600 /dev/scd0

```

---

