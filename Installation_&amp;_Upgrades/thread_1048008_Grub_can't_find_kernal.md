---
title: "Grub can't find kernal"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by And6ate9 on 2009-01-23
I got a multi-boot going with and grub partition pointing to a Intrepid menu.lst. The grub in intrepid is having a hard time find the kernels to boot. The entries are setup using UUID.
When I add and entry using dev/sda(x,y) grub seems to find the kernels without problems.

I just want to know how I can get ubuntu to change to the dev/sda entries for the kernel when updating instead of UUID.

thanks

---

### Post by sahabcse on 2009-01-23
I think we have to give the hard disk partition manually in menu.lst. For finding the root partition using the command mount
================================
 #mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /virtualbox type ext3 (rw)
==================================

---

### Post by logos34 on 2009-01-23
try editing the 'kopt' and 'groot' line to use '/dev/sdax' format instead of uuid:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR="Red"]# kopt=root=/dev/sda1 ro[/COLOR]

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
[COLOR="Red"]# groot=(hd0,0)[/COLOR]

also, change the 'root' line in the automagic section if it too uses UUID.

sudo update-grub

---

### Post by And6ate9 on 2009-01-23
oh silly me, who knew?

thanks

---

