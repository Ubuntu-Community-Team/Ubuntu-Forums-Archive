---
title: "where is udevinfo?"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by kudude on 2009-09-13
I'm a new user (here's my first post) migrating from 6 years of gentoo.  I'm trying to setup my filesystem right now.  I have a large external drive with several partitions that I want mounted via /etc/fstab.  The problem is I need udevinfo to tell me about the drive.  Even though the "udev" package is installed, running
"sudo udevinfo"
gets me a 
"command not found"
message.

Where is this elusive executable?

thank you

---

### Post by sisco311 on 2009-09-13
use udevadm instead.

```
udevadm info -q all -n /dev/sda1
```

you can list the partitions with:
```
sudo fdisk -l
```
or
```
sudo blkid
```

---

### Post by kudude on 2009-09-13
thanks for the quick help

---

### Post by Jose Catre-Vandis on 2010-01-02
> **sisco311 said:**
> use udevadm instead.

```
udevadm info -q all -n /dev/sda1
```

you can list the partitions with:
```
sudo fdisk -l
```
or
```
sudo blkid
```

Thanks, Useful stuff.

Question though..

Are the UUIDs for USB drives hard coded, or can they be changed, say if you reformat etc?

---

### Post by sisco311 on 2010-01-02
> **Jose Catre-Vandis said:**
> Thanks, Useful stuff.

Question though..

Are the UUIDs for USB drives hard coded, or can they be changed, say if you reformat etc?

Nope, UUIDs are not hard coded.

Yep, they change after a reformat.

You can use tune2fs to set a custom UUID.
```

man tune2fs | less +2/-U

```


It doesn't matters if it's an USB drive or not, partitions are partitions.

---

### Post by Jose Catre-Vandis on 2010-01-03
Thanks sisco311

---

