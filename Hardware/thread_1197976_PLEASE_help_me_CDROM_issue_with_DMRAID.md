---
title: "PLEASE help me CDROM issue with DMRAID"
date: 2009-06-26
forum: Hardware
---

### Post by joeelmex on 2009-06-26
Hello I am so close of having a 100 percent stable Ubuntu box.  I have an Asus G50VT laptop.  The laptop has a build in raid controller an intel and when I installed it, I have to enable dmraid=true during install in order for Ubuntu to see the raid partition.  Now this is my problem once Ubuntu is installed, if I place a CD or DVD in my cdrom dvd player, it will read it but if I try to unmount or eject it will just stop working.  I dont know what else to try.  The reason I am sure it has to do something with my raid is due to the fact I installed ubuntu on same laptop with raid disabled and everything worked including cd rom.  I then went back and re-installed with raid and same issue.  I can read a cd or maybe even 2 but then it will stop responding when it does these are the errors on my var/log/mesasages

```
Jun 26 21:06:36 R2D2 kernel: [10857.816212] ata2: hard resetting link
Jun 26 21:06:41 R2D2 kernel: [10863.180154] ata2: link is slow to respond, please be patient (ready=0)
Jun 26 21:06:46 R2D2 kernel: [10867.828168] ata2: hard resetting link
Jun 26 21:06:51 R2D2 kernel: [10873.188153] ata2: link is slow to respond, please be patient (ready=0)
Jun 26 21:06:56 R2D2 kernel: [10877.844143] ata2: hard resetting link
Jun 26 21:07:01 R2D2 kernel: [10883.208117] ata2: link is slow to respond, please be patient (ready=0)
Jun 26 21:07:31 R2D2 kernel: [10912.876630] ata2: limiting SATA link speed to 1.5 Gbps
Jun 26 21:07:31 R2D2 kernel: [10912.876636] ata2: hard resetting link
Jun 26 21:07:36 R2D2 kernel: [10917.900170] ata2.00: disabled
Jun 26 21:07:36 R2D2 kernel: [10917.900190] ata2: EH complete

```Gnome will give out errors of it cant be mounted and something else.  Please help me figure this out, I cant think of anything else to try.  

here is what shows when i type mount after my cdrom stops workings

> /dev/mapper/isw_cahdcfdaai_G50Vt2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/mapper/isw_cahdcfdaai_G50Vt3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joeelmex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joeelmex)


more info on the failing
> 10857.816203] ata2.00: status: { DRDY }
[10857.816212] ata2: hard resetting link
[10863.180154] ata2: link is slow to respond, please be patient (ready=0)
[10867.828156] ata2: COMRESET failed (errno=-16)
[10867.828168] ata2: hard resetting link
[10873.188153] ata2: link is slow to respond, please be patient (ready=0)
[10877.844131] ata2: COMRESET failed (errno=-16)
[10877.844143] ata2: hard resetting link
[10883.208117] ata2: link is slow to respond, please be patient (ready=0)
[10912.876616] ata2: COMRESET failed (errno=-16)
[10912.876630] ata2: limiting SATA link speed to 1.5 Gbps
[10912.876636] ata2: hard resetting link
[10917.900154] ata2: COMRESET failed (errno=-16)
[10917.900165] ata2: reset failed, giving up
[10917.900170] ata2.00: disabled
[10917.900190] ata2: EH complete



Ubuntu 9.04 64 bit

---

