---
title: "mount /dev/sdb1 works, but not with options utf8,gid,uid OR umask"
date: 2009-08-19
forum: Hardware
---

### Post by biggerben on 2009-08-19
I recently got a new 500GB S-ATA hard disk
after mkfs.ext4 /dev/sdb1 I mounted it and unmounted it without a problem.

Then I added following line to fstab:
```
UUID=9dd1a9a3-feea-450d-9aa9-cf24a05d9ffe /data ext4 defaults,utf8,umask=033,uid=1000,gid=1000 0 2
```

when I try to mount it then I get an error: mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.

dmesg says 
```

[ 1536.598541] EXT4-fs (sdb1): Unrecognized mount option "utf8" or missing value

```

If I leave out utf8 it complains about umask, uid or gid. If I leave options line at "defaults" it will mount.

I have a different partition on a different disk that I mount with the same opions, that works without any problems.

Why will mount not allow me such standard options on one partition but allow it an another?

---

### Post by DaithiF on 2009-08-19
Hi,
I'm @work so can't confirm this, but I would guess that defaults can't be combined with other options -- defaults is a shorthand way of specifying a list of options (**rw**, **suid**, **dev**, **exec**, **auto**, **nouser**, and **async)**.

so to combine with other options remove 'defaults' and include the options explicitly.

---

### Post by regala on 2009-08-19
> **DaithiF said:**
> Hi,
I'm @work so can't confirm this, but I would guess that defaults can't be combined with other options -- defaults is a shorthand way of specifying a list of options (**rw**, **suid**, **dev**, **exec**, **auto**, **nouser**, and **async)**.

so to combine with other options remove 'defaults' and include the options explicitly.

no really the question here...
you can't specify these options because these are here to paliate several lacks in Microsoft's ideas of filesystems: ownership, access rights...

you cannot but don't have to use uid=, gid=, and utf8 for native Linux filesystems like ext4, ext3, reiserfs, xfs...

---

### Post by biggerben on 2009-08-19
> **regala said:**
> no really the question here...
you can't specify these options because these are here to paliate several lacks in Microsoft's ideas of filesystems: ownership, access rights...

you cannot but don't have to use uid=, gid=, and utf8 for native Linux filesystems like ext4, ext3, reiserfs, xfs...

So you're saying the best way is to mount it with defaults then chown the mountpoint?

---

### Post by regala on 2009-08-19
> **biggerben said:**
> So you're saying the best way is to mount it with defaults then chown the mountpoint?

that's not what I'm saying. what I'm saying is that you have bad assumptions as to what can do your filesystem on Ubuntu.
It has full POSIX access rights support and as such, any file on it has an owner,group and access rights set up. So at creation, any file/directory/whatever on it belongs to root. 
IOW, You HAVE to change owner or access rights on the root directory of this filesystem, if you want some other user to be able to write on it. (and access rights are conserved across reboots, umounts, ... this is not Windows)

uid=,gid= options are just "workarounds" for filesystems lacking proper POSIX access rights, which is not really the case for a Linux native fs...

---

