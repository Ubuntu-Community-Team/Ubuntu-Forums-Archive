---
title: "Cannot get 2nd hard drive mounted"
date: 2010-08-14
forum: Hardware
---

### Post by mechanicalmetal on 2010-08-14
Hello,

Running 10.04 LTS x64.

I have 2 hdds, 1 primary TB hdd and secondary is a 500gb. Well before I had my TB hdd running winblows 7, and my 500gb drive running Ubuntu for a second os and also has all my music and files on it. 

I just formatted my TB hdd and I am running Ubuntu for my primary OS. Now my 500gb hdd will not even detect or mount. I can find it when I run Gparted, but I have no idea how to even mount it. The file system says its linux, but im completely lost.

Any ideas?

Its got all my pics and music on it ;(

---

### Post by oldfred on 2010-08-14
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You should review above to understand some of the setting available with the gui apps:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Some are now recommending mountmanager also in synaptic:

The basic functionalities of MountManager are:
  - Mount and unmount partitions (ext3/2, ntfs, swap, fat, reiserfs, iso9660,
  udf, ...)
 - Show all logical and physical disks

---

### Post by mechanicalmetal on 2010-08-15
Ive tried multiple things. Cannot get my hdd to mount :(

Any ideas? Sorry im a newb

---

### Post by oldfred on 2010-08-15
You keep saying hard drive. You do not mount a drive but the partitions in the drive.

Copy & Paste into your terminal & Post this:

```
sudo fdisk -l
```

---

