---
title: "unable to mount dvd"
date: 2017-01-13
forum: Hardware
---

### Post by freeworld4 on 2017-01-13
Error mounting /dev/sr0 at /media/tyler/STEP_UP_REVOLUTION_DANCE_WORKOUT: Command-line `mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8" "/dev/sr0" "/media/tyler/STEP_UP_REVOLUTION_DANCE_WORKOUT"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sr0,
missing codepage or helper program, or other error


In some cases useful info is found in syslog - try
dmesg | tail or so.

[ 3541.845992] UDF-fs: incorrect dstring lengths (33/32)

---

### Post by SeijiSensei on 2017-01-13
Is this a video DVD?  You cannot mount those because they don't contain a valid filesystem.  You have to use software like Handbrake to rip them, or watch them with a video player like SMPlayer or VLC.  See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more details.

---

