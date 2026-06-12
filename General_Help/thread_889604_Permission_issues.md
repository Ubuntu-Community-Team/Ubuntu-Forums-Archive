---
title: "Permission issues"
date: 2008-08-14
forum: General Help
---

### Post by ldclan on 2008-08-14
Well, I have an issue with Ubuntu and I feel it would be best if I tell what has been done so I can correct it.
I had NAS setup on a old PC using NASlite. It had over 350BG of data stored on it and the format of the drive is ext2.
Well I wanted something that could do backups to an external hard drive on that machine and Naslite doesn't support that.
So I decided to use a old 10GB hard drive and install Ubuntu 8.04 on it using the old NAS PC, (by the way during the install I had the original NAS hard drive disconnected so I would not accidentally format it).
Well the install went so well got the OS running, joined my work group and then I connected the original NAS hard drive with the 350GB of data on it.
When I connected it asks for my password the mount it, then I created a shared folder on that drive and moved the original NAS data into the newly created shared folder. No problem. I can see the shared folder  write to it, make modifications etc.

Well here is my problem:
The original NAS hard drive's contents have their original folder and file permissions so I can not modify them only read them with the shared folder.
I tried change the permissions but the sub folders and files do not inherit the parents permissions using the GUI. So it didn't work.
So I tried using the terminal to change it, but I do not know how to tell the terminal to change to the original NAS hard drive? It is mounted but it will switch to it.

When I type in mount in the terminal this is what I get:

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
/dev/sdb1 on /media/NAS_Disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

The drive is listed as /dev/sdb1 on /media/NAS_Disk-1 type ext2, but how do I get the terminal to switch to it so I can change its permissions?

Would someone be willing to help me? I want the original 350GB of data to inherit the parents (shared) folder permissions, so I make changes to the data as necessary. I need to change the owner, group and other permissions.

Any help would be greatly appreciated. Thank you.

---

### Post by jmkemp on 2008-08-15
Having just added a new HD myself all I had to do was open a terminal, change to the directory that it was mounted on and then change the permissions for the copied over files with chmod -r

In your case it would be something like:
cd /media/NAS_Disk-1
sudo chmod -r <permissions> <files>

---

