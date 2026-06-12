---
title: "Drive not mounting!"
date: 2010-01-23
forum: Hardware
---

### Post by toji on 2010-01-23
Hey i have karmic and suddenly it's not mounting one of my four partitions. it gives something like none mounted on none. it's got some imp. data so is there any way to fix it???:confused:

---

### Post by user1397 on 2010-01-23
> **toji said:**
> Hey i have karmic and suddenly it's not mounting one of my four partitions. it gives something like none mounted on none. it's got some imp. data so is there any way to fix it???:confused:type this in a terminal to see which drives you currently have mounted/more info on them:


```
df -h
```

---

### Post by toji on 2010-01-30
i did it..
it gives me this
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              24G  8.8G   14G  39% /
udev                 1003M  280K 1002M   1% /dev
none                 1003M  924K 1002M   1% /dev/shm
none                 1003M  188K 1002M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda5              30G   20G  9.4G  69% /media/disk
/dev/sda1              20G   16G  3.7G  82% /media/WINDUHS

there's another partition which it's not showing.

---

### Post by toji on 2010-01-30
i did it..
it gives me this
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              24G  8.8G   14G  39% /
udev                 1003M  280K 1002M   1% /dev
none                 1003M  924K 1002M   1% /dev/shm
none                 1003M  188K 1002M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda5              30G   20G  9.4G  69% /media/disk
/dev/sda1              20G   16G  3.7G  82% /media/WINDUHS

there's another partition which it's not showing.

---

