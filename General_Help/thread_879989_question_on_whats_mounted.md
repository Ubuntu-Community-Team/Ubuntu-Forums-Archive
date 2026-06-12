---
title: "question on whats mounted"
date: 2008-08-04
forum: General Help
---

### Post by mupto on 2008-08-04
ok, when i execute mount and it displays them all i used to only get the regular hard drive and linux and whatnot but now i get a crapload. and im wondering what it all is and what i did lol. even after restarts its still stayed the same. anyhelp would be appreciated thanks.

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mupto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mupto)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by K2712 on 2008-08-04
From the man page for mount:

```
mount [-l] [-t type]
```
lists  all mounted file systems (of type type).  The option -l adds the (ext2, ext3 and XFS) labels in this listing.

So basically entering mount by itself is the same as entering mount -l, which will list all filesystems that are currently mounted.  Keep in mind that in linux, everything is considered a file, included processes, devices, etc...

If you wanted to see all ext3 filesystems currently mounted it would be:

```
mount -l -t ext3
```

---

### Post by mupto on 2008-08-04
i guess my question wasnt too clear but what i wanted to reall yknow is what are all those entries, ive always just used "mount" by itself and it never listed all those. was mostly wondering how it all got there :/

---

### Post by K2712 on 2008-08-04
Sorry about that, I misunderstood your question.:oops:

I'm afraid I don't know the answer, but when I execute mount I get pretty much the same results.

---

### Post by caljohnsmith on 2008-08-04
I don't think you should be worried, muptu, all those are valid directories and processes that should be mounted. For instance, here's what I get when I run "mount":
```
john@TECH5321:~/.kde/Autostart$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-20-rt/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```
As you can see, much of those processes and directories are the same as your own. :)

---

### Post by crwmike on 2008-08-04
I believe some of them are virtual filesystems, the contents of those filesystems are in memory.:confused:

---

### Post by mupto on 2008-08-04
well thanks everyone, yea it could be something from my vmware. im not currently running this install virtual but i do use them.

---

