---
title: "Home folder missing after external HD mounted"
date: 2014-01-11
forum: Hardware
---

### Post by Drew012 on 2014-01-11
I'm running 12.04 LTS on my laptop, with an SSD where my */home/username* previously resided. The problem arised when I went to connect and mount a second hard drive. This second hard drive contained another 12.04 LTS filesystem, as well as a */home/username* folder with *the same exact username* as my installation on the SSD. The /home/ folder was also encryped on the hard drive (I don't recall selecting to encrypt it on the SSD however.)

Anyway, I followed this [http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu.html](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu.html) in attempt to decrypt and access the external HD I had just connected. After a few commands, I noticed the SSD showed that it was still mounted, however my */home/username/* directory was missing. My guess is that due to the same name of the users, it was overridden. Since this - I have been able to get root access on the SSD, where all of my other files remain - but the home/directory has been replaced by the /home/ of the external HD (which was basically empty.)

No idea where to go from here - am I screwed? It seems like there would be some sort of fallback (eg: switching to read-only on the SSD) to prevent this override from happening?


**$ mount**
```

username@laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
[B]/home/username/.Private on /home/username type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=e2d3cc4368494b7e,ecryptfs_fnek_sig=53f6809c0ef1309e)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)[/B]

```

**$ cat /etc/fstab | less**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=65bbc142-81ab-4037-97f1-ce0114c3946b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=5f53868d-51a9-46ce-a0db-aff8c916ae29 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```


Thanks - as always, let me know if more information is needed! =)

---

### Post by ajgreeny on 2014-01-11
First thing is not to panic !

I suspect that your original /home files and folders are still sitting where they were but are simply not being mounted any more, as the second drive is now somehow taking over the same mount point, and both /home folders or partitions can not use the same mount point.

You will need to unmount the second disk and its partitions, I think, but I am not sure how you can do that on your running system when logged in as that user.  A second user with admin permissions, or recovery mode from the grub menu may allow you to change the user name on that, though it is possible complicated by encryption about which I know absolutely nothing.

---

### Post by houstonbofh on 2014-01-11
The way encrypted partitions work is that they mount over your user home directory.  You need to tell it to mount elsewhere...  if you type "mount" from the cli you will see it, and may be able to move it manually.

---

### Post by Drew012 on 2014-01-11
You're right, the problem can be seen here:

```

$ mount
   ...
/home/drew/.Private on /home/drew type ecryptfs

```

Since this is being mounted inside of /dev/sda1 (mounted on root), it seems this is overriding it.
When I boot to safe mode CLI, nothing is mounted, and I can mount sda1, however, when I go to log back in (normal boot), the encrypted folder appears to be mounted again.
I'm not sure if my /etc/fstab is messed up? I'll be looking for other reasons this is auto mounting on boot I suppose?

---

### Post by houstonbofh on 2014-01-11
Yep.  You can use sudo to unmount it, and mount it in /home/drew/encrypted after you create a directory called "encrypted" in your home dir.  But you do need to see where it is auto mounting to fix it more permanently.

---

