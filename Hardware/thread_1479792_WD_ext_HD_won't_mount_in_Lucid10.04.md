---
title: "WD ext HD won't mount in Lucid/10.04"
date: 2010-05-11
forum: Hardware
---

### Post by Halfling Rogue on 2010-05-11
**SOLVED:** Manually mounting it as /dev/sdb1 to a folder worked. It's running really slow, but I think that's just because it's so large (160 gigs).

```
mount -t vfat /dev/sdb1 /mnt
```

--

I have a Western Digital external hard drive, model #WD1600U017-004. It's given me [a few]("http://ubuntuforums.org/showthread.php?t=512176") [problems in]("http://ubuntuforums.org/showthread.php?t=590437") [the past]("http://ubuntuforums.org/showthread.php?t=561630"), particularly with Windows machines, but it's been more or less reliably mounting in Hardy for a good long while.

I recently upgraded to Lynx on this machine (a Dell Latitude D600), and while the HD still automounts in Hardy (which I've kept installed), it absolutely refuses to show up in Lynx.

This is what mount -l gets me in Hardy when both my flash drive (Manzanita) and my HD (Huevosa) are mounted:

```
/dev/sda2 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-27-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/halflingrogue/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=halflingrogue)
/dev/sdb1 on /media/MANZANITA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush) [MANZANITA]
/dev/sdc1 on /media/LA HUEVOSA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush) [LA HUEVOSA]

```

I'm going to try manually mounting it in Lynx, but if anyone has any suggestions on how to get it working, I'd appreciate it. I really need to get at that data on my Lynx install.

---

