---
title: "External hard drive becomes read-only when perl script is run"
date: 2008-08-25
forum: General Help
---

### Post by typically on 2008-08-25
Hi all,

Really weird/irritating problem (Ubuntu 7.10): I have an external hard drive (VFAT) mounted and writable, but when I run a simple perl script which I've simplified to do nothing more than access and list folders on the mounted drive, it suddenly becomes read-only:

```

chdir $subject_dir;

@subjects = grep { -d } glob ( "*" );

```

If I unmount and remount it becomes writable again, but the perl script again changes it to read-only:

```

typically@typically-desktop:/$ sudo umount /dev/sdb1
typically@typically-desktop:/$ sudo mount -o uid=typically,gid=typically /dev/sdb1 /media/disk/
typically@typically-desktop:/$ cd /media/disk/
typically@typically-desktop:/media/disk$ mkdir test
typically@typically-desktop:/media/disk$ ./minc_to_analyze_all.pl
{code runs}
typically@typically-desktop:/media/disk$ mkdir r
mkdir: cannot create directory `r': Read-only file system

```

This must be a bug, or no?

---

### Post by typically on 2008-08-26
Still have made no progress with this.. perhaps it is a security feature?

---

### Post by jigsaws on 2008-08-26
What about
pwd
before mkdir r

Are you sure still in /media/disk/ ?

---

### Post by typically on 2008-08-26
Yes I'm still in /media/disk/

The command that is causing the change is not chdir but

```
@subjects = grep { -d } glob ( "*" );
```

---

### Post by typically on 2008-08-26
Also running "mount" tells me this disk is read-write. Very bizarre. I have had no trouble with this disk in either ubuntu or windows until now.

output of mount for sdb1:
```
/dev/sdb1 on /media/disk type vfat (rw,uid=1000,gid=1000)

```

---

### Post by jigsaws on 2008-08-26
Ok, but first line of script is:
chdir $subject_dir;
Try "pwd" to be sure that you are still in "/media/disk" after running script.

---

### Post by typically on 2008-08-26
$subject_dir is set to "/media/disk"; I've also taken that line out and still get the problem. Here's the sequence of my commands; pwd says I'm still in /media/disk:
```

typically@typically-desktop:/$ sudo umount /dev/sdb1
[sudo] password for typically:
typically@typically-desktop:/$ sudo mount -o uid=typically,gid=typically /dev/sdb1 /media/disk/
typically@typically-desktop:/$ cd /media/disk/
typically@typically-desktop:/media/disk$ mkdir test5
typically@typically-desktop:/media/disk$ ./minc_to_analyze_all.pl
typically@typically-desktop:/media/disk$ mkdir test6
mkdir: cannot create directory `test6': Read-only file system
typically@typically-desktop:/media/disk$ pwd
/media/disk
typically@typically-desktop:/media/disk$ 

```

---

### Post by jigsaws on 2008-08-26
Very strange. Looks like a bug.

And what about:
sudo mount
sudo cat /etc/mtab

Is it possible to remount it rw?
Or try to cd /media/disk ; mkdir test7

---

### Post by typically on 2008-08-26
Solved! Posting solution here in case it's useful.

First, I checked the /var/log/kern.log file (on the advice of the Perl ppl), and found this line:

```

Aug 26 14:44:50 typically-desktop kernel: [  176.616936] FAT: Filesystem panic (dev sdb1)
Aug 26 14:44:50 typically-desktop kernel: [  176.616944]     fat_get_cluster: invalid cluster chain (i_pos 0)
Aug 26 14:44:50 typically-desktop kernel: [  176.616951]     File system has been set read-only

```

So I ran 

```
fsck.vfat /dev/sdb1 -a -w

```

...which fixed the errors. All is good!

jigsaws thanks for your suggestions.

---

