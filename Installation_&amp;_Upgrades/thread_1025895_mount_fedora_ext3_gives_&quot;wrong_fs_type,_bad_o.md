---
title: "mount fedora ext3 gives &quot;wrong fs type, bad option, bad superblock&quot;"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by _axiom_ on 2008-12-30
This is the command I am running:
```
sudo mount -t ext3 -o defaults /dev/sdb2 /media/sdb
```

And I get:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Suggetions I have seen are to install nfs-common and portmap (no effect here), or running various fdisk like utils to "fix" the broken filesystem.  There shouldn't be anything broken about the filesystem, it is an old Fedora drive, and I can boot to it just fine if I plug it in alone.  I'd just like to get some old files off it.

Anything I should try?

---

### Post by stderr on 2008-12-30
Did you setup LVM on that drive?

---

### Post by caljohnsmith on 2008-12-30
Are you sure you are trying to mount the correct partition? How about posting:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by _axiom_ on 2008-12-31
Ha! Turns out it was LVM across two drives, and I was trying to mount them one at a time.

Thanks for the hint.

Instructions here worked for me to get them mounted:

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

---

### Post by stderr on 2008-12-31
Glad you got it sorted. For anyone else bumping into this thread, with a standard LVM volume you can enable it with

```
sudo vgchange -ay VOLUME_NAME
```

where VOLUME_NAME is what you see under /dev - e.g. you may have a structure such as /dev/VOLUME_NAME/home, /dev/VOLUME_NAME/boot etc.

You can then mount the individual sections as usual e.g.

```
sudo mount /dev/VOLUME_NAME/home /media/MOUNT_PT
```

---

