---
title: "Problems with MOUNT USB HDD in Jaunty"
date: 2009-10-03
forum: Hardware
---

### Post by diegosacch on 2009-10-03
I had 2 users Diegus (root privileges) and Beta on Jaunty and 2 partitions (Y and U) on a USB HDD. I wanted to have partition Y only mountable for user Diegus.
On desktop, I selected the icon of the mounted partition Y, I right-clicked and in the Volume tab I inserted, in the Settings-Mount Options, parameter user_id=Diegus  (other Mount Options were : rw,nosuid,nodev,group_id=0,allow_other,blksize=4096; Filesistem = fuseblk).
After disconnecting+reconnecting USB HDD the Y icon disappeared and the error "Invalid mount option while attempting to mount volume 'Y Part HDD_PackBell' " was displayed.

If I manually mount partition Y on the same mount point used for partition U (/media) also icon of partition U disappears from desktop, but I can access partition Y via the mount point (/media) where I can find the tree of partition Y. But partition U is not accessible via the mount point directory /media.

I'm quite confused . Any suggestions to mount properly the USB HDD partitions ?    

Thanks

Output of mount command after mounting manually partition Y (I presumed on the device /dev/sdb1):
  
>>>>>>>>>
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)e 
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/diegus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=diegus)
/dev/sdb2 on /media/U Part HDD_PackBell type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

>>>>>>>>><

---

