---
title: "Mount error: wrong wrong fs type, bad option, bad superblock,"
date: 2014-12-31
forum: Hardware
---

### Post by roelof2 on 2014-12-31
Hello,

I am trying to recover data from an old hard drive (so formatting is not an option), but when mounting it I get the following error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=258902&stc=1[/IMG]

I followed the instructions at these threads and this website:

[http://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694](http://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://askubuntu.com/questions/525243/why-do-i-get-wrong-fs-type-bad-option-bad-superblock-error](http://askubuntu.com/questions/525243/why-do-i-get-wrong-fs-type-bad-option-bad-superblock-error)
[http://unix.stackexchange.com/questions/22653/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-sdb-on-centos-6-0](http://unix.stackexchange.com/questions/22653/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-sdb-on-centos-6-0)
[http://ubuntuforums.org/showthread.php?t=839579](http://ubuntuforums.org/showthread.php?t=839579)
[http://serverfault.com/questions/321693/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-sdb-on-centos-6-0](http://serverfault.com/questions/321693/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-sdb-on-centos-6-0)

None of those threads worked.


Also when i try
```
 [COLOR=#000000]$ sudo e2fsck -f -b 32768 /dev/sdb3
[/COLOR]
```

It returns the following
```
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?

```

When I run
```
df
```

it returns the following
```
Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sdc1       227850556    9693140 206560156   5% /
none                    4          0         4   0% /sys/fs/cgroup
udev              4073056          4   4073052   1% /dev
tmpfs              816772       1412    815360   1% /run
none                 5120          0      5120   0% /run/lock
none              4083840      38404   4045436   1% /run/shm
none               102400         52    102348   1% /run/user
/dev/sdd          1939024     554400   1384624  29% /media/roelof/MP3 SPELER
/dev/sda3      1921605196 1497262832 424325980  78% /media/roelof/e4482a2e-fdd8-46e5-94c4-0dcaef802463

```

Also when I try to run 
```
$ sudo e2fsck -f -b 32768 /dev/sdb3
```

I get the following error:
```
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?
```

I tried to mount it like this:
```
$ sudo mount -t vfat dev/sdb3 /media/roelof/d802d556-68ba-4566-975c-25d8aa7d12bb
```

But that also returned an error:
```
mount: mount point /media/roelof/d802d556-68ba-4566-975c-25d8aa7d12bb does not exist
```

It could very well be that I misspelled something, because I'm still a beginner when it comes to Linux/Ubuntu, which means that I don understand most of the more complicated terms (please keep that in mind when posting a reply, it helps out a lot).
If you have an idea on how to solve this, please post a reply. Formatting is not an option, because I intend to retrieve the data from the harddrive.

---

### Post by weatherman2 on 2014-12-31
What kind of data is on the "old hard drive?"  Is it a Windows partition?  If so, stop trying to use the e2fsck command, which is only used for Linux partitions. 

How old is "old?"

Ubuntu will automatically detect the usual Windows partition types (NTFS, FAT32) and mount them automatically with the mount command, like:

```
sudo mount /dev/sdb3 /mnt
```

FYI, the second argument (/mnt in my case above) is a directory that must exist before you run the mount command.  In Linux, "/mnt" is a default directory for mounting other partitions and will already exist.

What is the output of the command

```
sudo parted -l
```

?

---

