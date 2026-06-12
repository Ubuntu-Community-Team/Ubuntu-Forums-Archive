---
title: "Ubuntu cant find my cd/dvd drive"
date: 2009-05-13
forum: Hardware
---

### Post by hoan on 2009-05-13
Well as the topic explains my ubuntu installation wont find my cd drive, it doesnt matter kind of medium i put in the drive it just wont find it.
The installation went just fine but now when it is installed i just wont get ubuntu to find any cd's/dvd's.
Since there is nothing wrong with the drive as far as i know since it worked fine on Windows and the installation worked fine i assume the problem is in the settings in the os.
So heres my fstab:
```
[SIZE=1]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=65c6b598-1923-47ed-87ac-9f3bad6126e9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=947684a0-ec8d-48b3-8bcd-1fa4f01955a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/SIZE]
```and here comes the mtab:
```
[SIZE=1]/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/hoa/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hoa 0 0[/SIZE]
```
If you see the probem please help me

---

### Post by steve01832 on 2009-05-13
Hi. Your fstab looks perfect. When you put a disk in the drive does it spin up or does it do nothing? What distro of Ubuntu are you using? Also, what kind of computer are you using?  From the fstab you posted, it should all be good. You may have an unusual brand cd drive that Ubuntu can't support. Let us know.

Steve

---

### Post by hoan on 2009-05-14
Well my drive spins up as it should and such, im at work now so dont know the kernel but i have the latest ubuntu 9.04 desktop verision up to date with update manager since of yesterday, and i use it on my laptop.
Its a Zepto znote6625wd. I can get the kernel verision and such when i get home from work if that can be of use, the brand of the drive is samsung.

---

### Post by steve01832 on 2009-05-14
Try putting a disk in the drive. Click Places. In the middle section see if it shows the disk drive there. If it does, click it and see if we can get an error message such as failed to execute child process. It could be as simple as adding the correct library dependencies to decrypt the media's contents.

Steve

---

### Post by hoan on 2009-05-14
well i dont have any cd to choose in the places menu so that ones gonna be kinda hard to perform

---

### Post by hoan on 2009-05-16
Tried reinstalling ubuntu and that didnt help either, seems like ubuntu cant recognize my cd/dvd drive at all for some reason, any one know how to fix this?

---

