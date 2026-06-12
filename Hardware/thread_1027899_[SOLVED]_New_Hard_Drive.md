---
title: "[SOLVED] New Hard Drive"
date: 2009-01-01
forum: Hardware
---

### Post by mikeyd612 on 2009-01-01
I just installed a new hard drive today. I have Ubuntu installed on one and am going to use the new one as storage. So nothing to do with the OS or anything. I formated it in ext3, and mounted it. However it seems that the system treats the new space as a directory. How do I get the system to see it as a disk and show up in the "Places" menu? Thanks

---

### Post by logos34 on 2009-01-01
remember: linux sees everything as a directory!

maybe you need to enable 'volumes_visible' option in gconf...But it should still show in the side pane in nautilus file browser.  Do you see it?

---

### Post by mikeyd612 on 2009-01-01
I remember back when I was researching linux before I was sure if I wanted to take the plunge, and saw that "everything in linux is a file" or something to that effect. But to answer your question, no. It's not in the side bar. Does it matter where the hard drive is mounted? I followed a couple tutorials online, and it didn't seem to matter but I'm not sure. It's mounted in "/hd" A directory I created.

---

### Post by taurus on 2009-01-01
But files are stored in directories.

Why don't you use a new mount point like /media/hd in /etc/fstab?

---

### Post by mikeyd612 on 2009-01-01
What do I need to do to re-mount it? The only thing I know I need to do is re-edit a file and change the path so that it is mounted on start up. I gotta find it again. But do I just say "mount /dev/sdb . . ." to it's new path and it'll be ok? I'm still a major noob to dealing with hardware, so you might need to explain it to me as if you were telling it to a 4 year old. Thanks

---

### Post by taurus on 2009-01-01
You would change the mount point in /etc/fstab.

```
gksudo gedit /etc/fstab
```
And of course, you need to create the new mount point or it won't be able to mount it next time you boot up.

```
sudo mkdir /media/hd
```

---

### Post by logos34 on 2009-01-01
> **mikeyd612 said:**
> What do I need to do to re-mount it? ...do I just say "mount /dev/sdb . . ." to it's new path and it'll be ok?

do like taurus said, then it will automount at boot at new dir.  And you really should put any other new mount points in /media (besides, that's the default, used to be /mnt)

To remount without reboot:

sudo umount /where/partition/is/now/mounted

sudo mount -t ext3 /dev/sd?? /media/hd

---

### Post by mikeyd612 on 2009-01-02
Thanks I guess it was just where it needed to be mounted everything is good. Thanks guys

---

