---
title: "DVD drive writes, but does not read discs. HELP!"
date: 2010-12-14
forum: Hardware
---

### Post by NealCrosby on 2010-12-14
I'm fairly new to Linux, and I am having trouble with my DVD drive.  It will write, but it doesn't read media.  Here is my "sudo lshw" output:

description: DVD-RAM writer
                product: DVD RW AD-7586H
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/SUNSHINE
                version: KH03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/SUNSHINE
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

As you can see, it detects the media, it just doesn't read it.  I have all the copy-protection packages installed (I believe).

Any thoughts on what to try next?

---

