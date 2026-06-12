---
title: "how to umount devices via terminal?"
date: 2008-10-24
forum: General Help
---

### Post by SOULTE on 2008-10-24
hi bros. it's my first post here because my search about unmounting devices in ubuntu didn't returned good results. plz inform me about that. thx.

---

### Post by SOULTE on 2008-10-24
oh what a funny mistake! just found i was trying to unmount with **_un_mount** command not **_u_mount**!! sorry.

---

### Post by kpkeerthi on 2008-10-24
```
sudo umount <mount-point>
```

To see the mount points, run this command:
```
mount
```

---

### Post by SOULTE on 2008-10-24
> **kpkeerthi said:**
> ```
sudo umount <mount-point>
```

To see the mount points, run this command:
```
mount
```
thx dude.

---

### Post by GuyZerO on 2009-08-27
sorry for bumping an old thread if thats a problem.

i was googling how to unmount drives and i came across this thread. it almost helped me out but i still have some issues. my iphone got mounted like five times while using itunnel... so i was wondering how exactly i would un mount this drive

...```

mount.fuse.ifuse on /media/iPhone type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
mount.fuse.ifuse on /media/iPhone_ type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
mount.fuse.ifuse on /media/iPhone__ type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
mount.fuse.ifuse on /media/iPhone___ type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
mount.fuse.ifuse on /media/iPhone____ type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
mount.fuse.ifuse on /media/iPhone_____ type fuse.mount.fuse.ifuse (rw,nosuid,nodev,allow_other)
guy0203@guy0203-pc:~$ sudo umount fuse.mount.ifuse

```

yeah if any one has any ideas it would be much appreciated

---

### Post by GuyZerO on 2009-08-28
never mind. i was making a stupid mistake and using the wrong information... all resolved now

---

### Post by chepe263 on 2012-01-17
let's say someone google and found here because is using ifuse

you must install ifuse first

then create a folder on your home like

mkdir iphone

then run

ifuse /home/<user>/iphone -s

add --root if you want access to the whole iphone filesystem. I guess you must have the device jailbroken before using ifuse

if you try to unmount the iphone using nautilus it says you don't have enough permissions so open a terminal and type

sudo umount /home/<user>/iphone

and your are ready

hope this helps, this worked for me 6min ago

---

### Post by winchendonsprings on 2012-01-17
What is the exact command that nautilus uses if you "safely eject drive?"

It spins down drive before unmounting.  

umount compined with hdparm something?

---

