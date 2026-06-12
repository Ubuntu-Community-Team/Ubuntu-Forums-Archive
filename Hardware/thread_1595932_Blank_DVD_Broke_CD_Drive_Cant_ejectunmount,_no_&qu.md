---
title: "Blank DVD Broke CD Drive? Cant eject/unmount, no &quot;cdrom&quot; device"
date: 2010-10-13
forum: Hardware
---

### Post by lxnski on 2010-10-13
Dear forum,

Last night I attempted to burn a dvd-cd but 1/2 way through the burn I got an error message and ejected the dvd. I took out the dvd and put it back in, to see if maybe anything would run or if anything was saved. The computer could not read the dvd and nothing happened. I rebooted Ubuntu, it took a long time to boot up (as it attempted numerous times to read the dvd, I guess) with no luck. There is no CD recognized in "my computer". 

When I type "eject" in terminal I get: "unable to find or open device for: `cdrom'

similarly, the command "mount" gives me:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dmitry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dmitry)

```

This is a laptop and my eject button is not working either. 

Am I going to have to resort to taking apart my laptop? 

Please help..



Thank you in advance,
lxnski

---

### Post by irv on 2010-10-13
On most laptop the CD/DVD drive is easy to remove. A few screws on the bottom, and drive will slide out. It might be simpler then you think.

---

