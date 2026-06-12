---
title: "Cannot automount NTFS USB drive with /etc/fstab entry"
date: 2010-08-06
forum: Hardware
---

### Post by unc0nn3ct3d on 2010-08-06
I am running Ubuntu 10.04 with the latest version of ntfs-3g and I want to automount my external USB NTFS hard drive.  

The kicker is that I need it to mount with the 'sync' option enabled, which means I need an entry for this drive in my /etc/fstab and as soon as I have that entry in the fstab file I receive the 'Only root can mount..' error box when I plug in the drive.

I have run the gambit with this, doing everything that's been posted, and still it's spitting this error message at me.


This is my /etc/fstab entry: **/dev/disk/by-label/bertha /media/bertha ntfs-3g sync,rw 0 0**

although I have tried it with various options


This is my version of NTFS-3G:

[b]ntfs-3g 2010.5.22 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off
[/b]

I have tried compiling ntfs-3g with internal and external FUSE libraries, editing my /etc/fuse.conf to allow users to mount

I have followed the instructions herE: [http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged](http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged)
I have added my user account to the 'disk' group
I have made sure that I have perms to the mount point

I'm at my ropes end after spending my entire afternoon trying to resolve this.. Any help at all would be greatly appreciated

---

