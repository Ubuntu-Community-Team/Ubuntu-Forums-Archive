---
title: "NTFS and fuseblk"
date: 2008-07-05
forum: Hardware
---

### Post by JonWasHere42 on 2008-07-05
I am sure questions like this one have been answered before, but I have searched for a solution to this problem and have come up empty.

I have a dual booted laptop. Running hardy/vista. Well I can mount the vista volume as fuseblk, and write to it, and allow all users to read from it, and everything is wonderful. Except I dont want that.
My laptop is used by several people, (via ssh and local). I have set each one up with their user and groups, and set permissions and everything is all set up over there.

Except when anyone logs in, they can access and write to the vista partition. Now as a matter of principle i do not like this. So i have gotten the ntfs-config package. And that makes things worse by allowing everyone to write to my other partition. So with out that here is my entry in fstab:

> UUID=[UUID] /media/vista ntfs async,atime,nodev,noexec,auto,nosuid,owner,ro,uid=1000,gid=1000,umask=277 0 0


I have tried this with auto and noauto.

anyway when it mounts, (either automatically, or manually, whether i use the fstab or mount) it ALWAYS mounts with these options:

> /dev/sda3 /media/vista fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0

or using ntfs-config:

> /dev/sda3 /media/vista fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0

Any ideas?
--Jon

---

