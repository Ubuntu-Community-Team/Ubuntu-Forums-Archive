---
title: "Can't find CD drive"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by cactaur on 2007-05-05
So, back before I updated to Feisty, I had [this]("http://ubuntuforums.org/showthread.php?t=393611") problem. When I updated to Feisty, it was fixed and CDs were automounted and everything was fine. However, when I turned on my computer last night and put in a CD, it didn't detect it. I tried to go in with Nautilus, an all-too-familiar error message came to me:

```
Unable to mount the selected volume
mount: must be superuser to use mount
```

There was one time when I booted up where the CD was detected on the Desktop for 30 seconds, and then it disappeared, and was once again lost.

Now, my previous workaround was to manually mount the CD drive:

```
sudo mount /dev/hdc
```

However, now there is no /dev/hdc or /dev/cdrom. I have no idea where my CD drive went. /media/cdrom is just empty, and I don't see any other indication of where it could have disappeared to, and what brought it on to disappear in the first place. I haven't installed graveman on Feisty.

Here is my /etc/fstab if it is any help:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=8f68eeb3-71ad-4a2b-b18b-732f9bbe0f6a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=3785601e-7b94-4acd-9334-9eb515a8163a none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdb1    /media/backups vfat  iocharset=utf8,umask=000  0    0 -- not needed to regularly backup filesystem
```

I've noticed that fstab depends on /dev/hdc being where it should be. Does anyone have any idea where it could have disappeared to?

---

### Post by cactaur on 2007-05-05
RESOLVED

Turns out I might have knocked the wires that connect my CD drive to the motherboard loose while digging in my computer. I'm not sure whether I like it or hate it when I solve my own problems.

---

### Post by exoasol on 2007-05-08
I am having this same problem but my wires are not loose

---

