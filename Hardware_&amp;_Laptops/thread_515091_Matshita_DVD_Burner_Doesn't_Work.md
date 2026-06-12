---
title: "Matshita DVD Burner Doesn't Work"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by bgh10788 on 2007-08-01
I am having a problem using the CD-RW/DVD-RW drive in my computer. I go to Places-->Computer and click on the drive (with a CD or DVD in it) but it says...

Unable to mount the selected volume.
Show more details...
mount: special device /dev/hda does not exist

I have tried various CD's and DVD's with the same result. I installed from a LiveCD and use it all the time in Vista (dual boot). It is a laptop drive made by Matshita.  The exact model is:

Matshita DVD-RAM UJ850S ATA Device (according to windows device manager)

I have taken the following steps to try to fix it...

-Replaced "/dev/hda" with "/dev/cdrom" in /etc/fstab
-bash: /dev/scd*: No such file or directory
-sudo mount /dev/cdrw /media/cdrom0
-sudo mount /dev/cdrom /media/cdrom0
-sudo mount /dev/dvd /media/cdrom0
-looked through "lshw -short" and could not find it

Thank you!

---

### Post by pbcartwright on 2007-08-01
/dev/hda is probably your primary drive
here is what I get when I type the mount command, with a CD in the drive:
> mount
/dev/sda6 on / type ext3 (rw,acl,user_xattr)
/dev/sda7 on /home type ext3 (rw)
/dev/sda2 on /windows/C type ntfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sr0 on /media/Ubuntu 7.10 i386 type iso9660 (ro,nosuid,nodev,noatime,uid=1003,utf8)

so my CDROM is really /dev/sr0

try inserting an audio CD, or ANY LiveCD, then type :
mount
and see what is shows.
if nothing, try doing the mount command with /dev/sr0

---

### Post by bgh10788 on 2007-08-01
mount gives me this:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


"sudo mount /dev/sr0 /media/cdrom0" gives me this:

mount: special device /dev/sr0 does not exist

---

