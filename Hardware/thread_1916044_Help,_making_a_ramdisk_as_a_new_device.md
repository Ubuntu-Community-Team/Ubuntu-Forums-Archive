---
title: "Help, making a ramdisk as a new device?"
date: 2012-01-27
forum: Hardware
---

### Post by fidde88pven on 2012-01-27
Hi!

As the titles says; I it possible to mount a new device and then asign it to be a ramdisk and have it start each time the computer starts?

I know all about loss when computer shuts down, and have scripts for that.


Thanks in advance!

---

### Post by Lars Noodén on 2012-01-27
There are two ways to do that, [ramfs and tmpfs](http://www.thegeekstuff.com/2008/11/overview-of-ramfs-and-tmpfs-on-linux/).  To make it appear each time you boot, you need to have an entry in [/etc/fstab](http://manpages.ubuntu.com/manpages/oneiric/en/man5/fstab.5.html)

---

### Post by fidde88pven on 2012-01-27
Thanks, but where does it show me how to mount a new device? I dont want it on a folder "in" the harddrive, rather a new device name...?

Best regards.

---

### Post by fidde88pven on 2012-01-27
No one? :)

---

### Post by Lars Noodén on 2012-01-28
> **fidde88pven said:**
> Thanks, but where does it show me how to mount a new device? I dont want it on a folder "in" the harddrive, rather a new device name...?

Best regards.

It has to mount one a mount point somewhere.  However, you can choose where.

The /etc/fstab entry for a 20MB tmpfs partition could look something like this:

```

tmps  /mntpoint  tmpfs  rw,nodev,size=20m  0  0

```

---

