---
title: "unable to mount the volume"
date: 2009-02-17
forum: Hardware
---

### Post by sridarshan on 2009-02-17
when i shut down my computer last time , i dont remember what i did!
now whenever i try to open my 52.4gb drive(that is c drive )
i get an error message 
"unable to mount the volume"
:$log file indicate unclean shutdown(0,0)failed to mount  '/dev/sda1':operation not supported mount is denied because NTFS is marked to be in use ....."

help i'm a complete newbee!!

---

### Post by JaredDoggy on 2009-02-21
The reason for your problem is most likely shutting down windows wrong.  If you restart windows and shut down properly you should be fine if this is your problem.

I am having a similar problem but mine is a chicken and egg type scenario which is making it exceptionally difficult.  My windows will not start due to missing the file system32\hal.dll (aka my system is corrupt i believe due to a virus).  I shut down wrong because my system was freezing and can now only boot in ubuntu.  While in ubuntu I cannot access my hard drive via the same error to replace the file.  Here are status reports which I believe could be helpful to anyone nice enough to help me.  Thanks.

BTW ive been trying alot of force mount commands which have so far been unaffective but I cannot be sure if I am typing them in right.  

sudo mkdir /media/externaldisk
sudo mount /dev/sdb1 /media/externaldisk  

A command in which I could load and close down windows from Ubuntu would be helpful but I doubt such a command exists/would work anyway.  Please help.. again here are the reports.

ubuntu@ubuntu:~$ cat /etc/mtab
/proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/scd0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda2 /media fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
ubuntu@ubuntu:~$

---

