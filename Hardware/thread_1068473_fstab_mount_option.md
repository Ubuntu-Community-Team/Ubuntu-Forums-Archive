---
title: "fstab mount option"
date: 2009-02-12
forum: Hardware
---

### Post by toddvalentine on 2009-02-12
I have an internal HD hosting much of my data, music, photos etc. Immediately after installing 8.04 I edited my fstab to include this:

```
/dev/sdb1    /media/bully    jfs    auto,rw,user    0    0
```

The drive mounted and worked flawlessly until just recently and now I receive error messages that I have an invalid mount option. I changed fstab options to see if I couldn't find the invalid option, but I cannot seem to mount the drive.

---

### Post by toddvalentine on 2009-02-13
Still checking options after editing fstab:
```
UUID=6be52602-a9eb-4ba0-98e1-191402dfa918	/media/bully	jfs	defaults	0	0
```
This also doesn't work when attempting to mount.

---

### Post by toddvalentine on 2009-02-13
When I remove that line from fstab and attempt to mount (in nautilus as root) I get this message:
```
mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error 
```

---

