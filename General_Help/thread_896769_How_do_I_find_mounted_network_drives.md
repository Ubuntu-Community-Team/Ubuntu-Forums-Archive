---
title: "How do I find mounted network drives?"
date: 2008-08-21
forum: General Help
---

### Post by theilliniguy on 2008-08-21
When looking to OPEN inside some aps (VLC for instance) all I ever see is HOME, DESKTOP, etc.  I don't see a mounted network drive.  How do I navigate to that mounted network drive?

---

### Post by Titan8990 on 2008-08-21
If you have not mounted the network drive then it is not mounted. To view everything that is mounted:

sudo mount

---

### Post by theilliniguy on 2008-08-21
> **Titan8990 said:**
> If you have not mounted the network drive then it is not mounted. To view everything that is mounted:

sudo mount

Did that and pasted results here:

/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sde1 on /media/EEEPC type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

It shows as Mounted Volume hdd_a on dlink-6d2729 in File Explorer though.  Is that not the same?  I can open it in some aps - just not all.

---

### Post by Titan8990 on 2008-08-21
Right click on the drive in file explorer, unmount and then mount it again.

---

### Post by theilliniguy on 2008-08-21
> **Titan8990 said:**
> Right click on the drive in file explorer, unmount and then mount it again.

Thanks for helping.  OK - did that.  Opened VLC and tired OPEN FILE and no network drive listed.

---

