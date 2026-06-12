---
title: "External Hard Drive"
date: 2010-07-30
forum: Hardware
---

### Post by Ronan5557 on 2010-07-30
So my last hard drive crashed and with my new one I installed Ubuntu. However, I am unable to access my external hard drive so I can transfer all my old files.

When I type "mount" into the Terminal I get this:

blair@blair-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/blair/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=blair)
blair@blair-laptop:~$ 

I assume that means I need to install the correct driver, and if I do where would I find it?

---

### Post by mr clark25 on 2010-07-30
do you know the drive number of your external hard drive? (probably not)

if you only have one ard drive in your system with one partition (excluding swap space), your exteranl drive would probably be at /dev/sdb1

try this:
```

mount /dev/sdb1

```but, if you look at the first line, it looks like there are some errors mounting /dev/sda1.
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro)

```is it safe to assume that /dev/sda1 is your partition that you have ubuntu installed on?

im not great with this kind of stuff, so im not sure that  is an error message.

---

### Post by Ronan5557 on 2010-07-30
I tested the external hard drive on a computer running windows, just to make sure it worked. It does. Then I tried it again on my Ubuntu-running computer, and miraculously it works. So yea, case closed.

---

