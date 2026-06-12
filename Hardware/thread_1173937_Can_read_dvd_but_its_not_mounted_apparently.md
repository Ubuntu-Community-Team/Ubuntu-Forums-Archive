---
title: "Can read dvd but its not mounted apparently"
date: 2009-05-30
forum: Hardware
---

### Post by kempy1000 on 2009-05-30
Hi

I have been trying to sort an anoying stutter that happens when i watch a dvd on my mythtv system.
I was lead to DMA, after looking at it i thought i will try enable it so following the ubuntu guide ([https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)) i issued the command:
```

sudo mount | egrep 'udf|iso9660'

```

However there was no output what-so-ever.
So i ran:
```

sudo mount

```

And the output was:

```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /var/lib type xfs (rw)
/dev/sdb1 on /media/harddrive2 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

No were in there i can see my IDE dvdrw drive?

So went into mythtv played the dvd with its stutter and the same command gave the same output!

Does this mean im reading from an unmounted drive? :-?
And could this be what is causing the anoying stutter?

Thanks
Chris

---

### Post by Vardaan Aggarwal on 2009-05-30
ya sometimes it happens with me also . Why don't u contact the ubuntu staff[FONT="Comic Sans MS"][/FONT]

---

### Post by kempy1000 on 2009-05-30
> **Vardaan Aggarwal said:**
> ya sometimes it happens with me also . Why don't u contact the ubuntu staff[FONT="Comic Sans MS"][/FONT]

How do i do that?
Thanks

---

