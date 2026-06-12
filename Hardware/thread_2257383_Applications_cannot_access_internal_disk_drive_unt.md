---
title: "Applications cannot access internal disk drive until I open it in file browser"
date: 2014-12-19
forum: Hardware
---

### Post by maverick.edberg on 2014-12-19
I have a large internal hard disk drive (not the drive the os is on) that I use to store games, media, etc. The drive is set up to be mounted automatically on system boot in the drives application (I verified this). Despite this, applications such as Steam or Rythmbox cannot see the content of the drive after boot unless I actually go over to the application tray and click on the drive to open it in the file browser first. As soon as I do this all of the content is immediately recognized by the applications. Can anyone point me in the right direction here as to why this might be happening? It isn't the end of the world but is slightly annoying and strange.

Thanks in advance.

---

### Post by weatherman2 on 2014-12-19
How have you verified that the drive (really a partition on the drive) is really mounted automatically?

Here's how I would verify it:

Reboot, then immediately open a terminal (Ctrl Alt t) and type

```

df

```

Is your big drive's partition listed there as mounted?  If not, it isn't.

---

### Post by oldos2er on 2014-12-19
I'd say "Drives" is mistaken if it thinks the partition is automounting, obviously it isn't. Usually if you want a partition mounted at system startup you would need to add it to your /etc/fstab file. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you need help configuring fstab, please post back. And before you do anything, make a backup copy! ```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by maverick.edberg on 2014-12-19
Apparently turning on auto mount changed the location of the mount, I discovered this using the df command in terminal. In editing 
/etc/fstab.backup

I was able to get it pointed to the right location.

---

