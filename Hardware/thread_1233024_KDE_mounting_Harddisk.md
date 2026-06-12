---
title: "KDE mounting Harddisk"
date: 2009-08-06
forum: Hardware
---

### Post by simonyee04 on 2009-08-06
Hi,  How do I check the Drive Letter in KDE?  How do I mount my harddisk to see the contents in KDE?  Please provide me with proper step by step. Thanks I am a newbie.

---

### Post by slakkie on 2009-08-06
Linux knows no such thing. 

You can check with the mount command what is mounted and where:

```

mount

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
//xxx.xxx.xxx.xxx/data$ on /mnt/samba/office-server/wndsrv002 type cifs (rw,mand)

```

If I would mount my external disk I would do mount /dev/sdb2 /mnt/addy/ext 

and that disk can then be accessed by going to /mnt/addy/ext


See also:
[http://www.google.com/search?q=mounting+disks+linux](http://www.google.com/search?q=mounting+disks+linux)

---

### Post by simonyee04 on 2009-08-06
/host/ubuntu/disks/root.disk on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sy1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sy1)

---

### Post by simonyee04 on 2009-08-07
Hi,

I am sorry but when I type ' ls /dev/sda*'

sy1@ubuntu:~/Documents$ ls /dev/sda*
/dev/sda  /dev/sda1
I want to list the content of the drive before I mount and unmount it.

How do I do that ?

Thanks
Simon Yee

---

### Post by simonyee04 on 2009-08-07
Dear Ubuntu Forum people, 

When I type 

sy1@ubuntu:/dev/disk/by-uuid$ sudo lshw -businfo -C disk
[sudo] password for sy1: 
Bus info          Device      Class       Description
=====================================================
scsi@4:0.0.0      /dev/sdc    disk        40GB WDC WD400JB-00JJ
scsi@4:0.1.0      /dev/cdrom  disk        CD/DVDW SH-S182F
                  /dev/cdrom  disk        
scsi@0:0.0.0      /dev/sda    disk        80GB ST380013AS
scsi@1:0.0.0      /dev/sdb    disk        80GB ST380817AS
I want to mount sdb not sda1

ls /dev/sda*
/dev/sda  /dev/sda1

How to unmount and mount the right drive?

Thanks
Simon Yee

---

