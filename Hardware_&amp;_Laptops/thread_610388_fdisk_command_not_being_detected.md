---
title: "fdisk command not being detected"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by unerau on 2007-11-11
i have tried to use the fdisk, but it doesnt recognize any of my drives. i put mount to see my drives and it said:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
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

notice the error in /dev/sda1 , is this supposed to be normal?
how can i remount it? when ubuntu wont recognize the command? or is it just supposed to not show anything on the command line.

thank you for your time

---

### Post by Linicks on 2007-11-12
You need to run fdisk as root (sudo).

Nick

---

