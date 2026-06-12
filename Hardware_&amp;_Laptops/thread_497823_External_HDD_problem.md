---
title: "External HDD problem"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by kaktuskatta on 2007-07-10
Hi! I have an external LaCie 320GB USB disk that doesn't show up anymore. The disk works under windows, and dmesg gives this output: 
[   38.444000] usb 5-7: device not accepting address 4, error -110
[   38.556000] usb 5-7: new high speed USB device using ehci_hcd and address 5

As already mentioned, the disk used to work, but now it doesn't.

output of mount:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
/dev/mapper/sda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
tmpfs on /dev/shm type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

output of fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9433    45054292+  83  Linux
/dev/sda3            9434        9729     2377620   82  Linux swap / Solaris


output of /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=70684943-bdec-4f25-a5fb-9cc292443dbc / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=BCA8BB45A8BAFD48 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=69e3b729-ba40-4800-b5ff-5696cbb30460 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
tmpfs     /dev/shm      tmpfs   defaults                 0      0

The disk worked after the upgrade to Feisty, and I can't remember doing something (stupid) for this to happen. The disk is formatted to ext2.

Hope this info is sufficient.

kaktus

---

### Post by espo111 on 2007-07-10
i just went through something like your mess,

check it out
[http://ubuntuforums.org/showthread.php?t=497154](http://ubuntuforums.org/showthread.php?t=497154)


also try unplugging all USB devices, except you drive and reboot.

see if it shows up in the terminal

lsusb

---

### Post by espo111 on 2007-07-10
i just went through something like your mess,

check it out
[http://ubuntuforums.org/showthread.php?t=497154](http://ubuntuforums.org/showthread.php?t=497154)


also try unplugging all USB devices, except you drive and reboot.

see if it shows up in the terminal

lsusb

---

