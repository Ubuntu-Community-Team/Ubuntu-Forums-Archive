---
title: "/ is mounted and working but does not appear in `mount` or `df -h`"
date: 2008-09-08
forum: General Help
---

### Post by ph8 on 2008-09-08
Here's a head scratcher; according to 'mount' my root partition isn't mounted on my home desktop - this is how it always is. Obviously it's mounted properly as i'm using it for desktop, home dir, documents - everything - mount -a doesn't help - what's not working?

A typical `mount`:

henri@osiris:~$ sudo mount
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdd1 on /mnt/redbrick type ext3 (rw,noexec,nosuid,nodev)
/dev/sdb2 on /mnt/horus type ext3 (rw,noexec,nosuid,nodev)
/dev/sdc1 on /mnt/isis type ext3 (rw,noexec,nosuid,nodev)
/dev/sda1 on /mnt/windows type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
//1.2.4.17/username on /mnt/hudson type cifs (rw,mand)

And my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# Main OS Partition
UUID=fe351cf5-a424-4949-ae46-843b5d3186b8 /               ext3    defaults,errors=remount-ro 0       1

# System Swap
UUID=d71c8cf4-d68d-429a-b7b1-673f8db035dd none            swap    sw              0       0

# DVD Drive
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Custom HDD Config

# Freecom
UUID=8cb6657d-7a75-40cb-be25-682910fd4325	/mnt/freecom	ext3	 defaults,user,auto 0 0

# Trans
UUID=4560-3EE3	/mnt/trans	vfat	defaults,user,auto 0 0

# Redbrick
UUID=f7615024-2b20-471f-9541-9cfd7326f5cf	/mnt/redbrick	ext3	defaults,user,auto 0 0

# Horus
UUID=12ce51c5-3a5a-45da-9d75-b82d9277fc5b	/mnt/horus	ext3	defaults,user,auto 0 0

# Isis
UUID=48fcbdfb-24b3-45ee-8a5d-bc06703ec004	/mnt/isis	ext3	defaults,user,auto 0 0

# Windows
UUID=2E96316796313127	/mnt/windows	ntfs-3g	defaults,user,auto,nls=utf8 0 0

# Durham JDrive

//1.2.4.17/username  /mnt/hudson     smbfs   rw,defaults,uid=1000,workgroup=mds,label=hudson,credentials=/home/henri/.nondescript,auto       0       0

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

