---
title: "hard drive will not boot or mount"
date: 2008-07-27
forum: Hardware
---

### Post by Theo148 on 2008-07-27
My laptop uses an 80 GB Western Digital Scorpio hard drive with 3 partitions - one for Windows, one for Ubuntu, and one swap. Recently, it abruptly lost power when starting up (displaying the GRUB menu) and on a subsequent attempt to start it failed to boot from the hard drive. The BIOS detects the hard drive as an IDE device (which is correct) but doesn't seem to be able to read from it (manually selecting the hard drive to boot fails, and no primary hard drive is listed in the BIOS setup). I loaded a Hardy LiveCD, and it detects the hard drive as an SCSI Drive, but is unable to mount it. 'fdisk -l' comes up blank.

I'm wondering if this is an MBR issue or a hardware problem, and if there's any way I can fix it without replacing the hard drive. Any help would be greatly appreciated.

---

### Post by Rocket2DMn on 2008-07-27
If the LiveCD cannot detect it, I would say it is a hardware problem.  I suggest disconnecting the power plug, removing the battery, then popping out the hard drive.  Wait a few moments, pop the drive back in (carefully), put in battery and plug in power.  Attempt to boot again.
If that fails, put the LiveCD in and post the output of the following commands (even if it is blank):
```
sudo fdisk -l
sudo blkid
mount
```

---

### Post by Theo148 on 2008-07-27
No luck so far - the boot still fails after removing and replacing the hard drive.

'sudo fdisk -l' comes up blank

'sudo blkid' gives me:
```
/dev/loop0: TYPE="squashfs"
```

'mount' gives me:
```
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```

---

### Post by Rocket2DMn on 2008-07-27
OK, it sounds like your hard drive or hard disk controller is dead.  If you can pop the drive into another laptop or an external 2.5" case, that might be worth the effort.  It just seems strange that the drive doesn't show AT ALL, which leads me to believe it may be a problem with the controller or motherboard rather than just the hard drive.  That's just an intuition though, it is quite likely that the hard drive just died and needs to be replaced.

---

### Post by Theo148 on 2008-07-30
Unfortunately trying the hard drive in anther computer didn't work either - I guess this means I should be looking for a new HDD. :( Oh well, that's what backups are for I guess.

Thanks for the help anyway! :)

---

