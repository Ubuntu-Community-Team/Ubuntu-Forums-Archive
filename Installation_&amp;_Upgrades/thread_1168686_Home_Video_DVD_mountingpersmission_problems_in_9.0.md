---
title: "Home Video DVD mounting/persmission problems in 9.04"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by bakechad on 2009-05-24
I have a bunch of DVDs that were converted from HI-8 tapes by the local video conversion store.  The ones he did years ago play everywhere, every way, etc.  The more recent ones have always worked a little strange.  On 7.10 I was able to mount them, watch them, copy them, etc.  Since moving to 9.04 I can only mount and view them with sudo.  I can't copy them no matter what I do.  I haven't discussed my problem with them, because they do not seem very technical.  They know how to use their “conversion” machine, but that seems to be the limit of their knowledge.  I regret using these guys, but would rather not spend $100s more to have these redone somewhere else.

Facts about the "problem" DVDs

- They play in most DVD players
- My son's Windows machine won't load them at all
- The mostly worked on 7.10
- 9.04 info below

The facts on 9.04:

- I can mount, play, copy, rip, etc. CDs with no problems
- Data DVDs mount normally with correct permissions
- Commercial DVDs mount and play correctly
- I have all restricted codecs installed (not that it should matter for my home movies)
- Permissions for everything except my “problem” DVDs are rx.  The “problem DVDs are only r. (see examples below)
- I can sudo to mount play my “problem” DVDs and view the directories.  I cannot copy them at all.

**FSTAB**
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=36cebb6d-07d7-4c6f-8e48-c1cd4750398a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d4b42599-56e8-4638-8524-6f73dc264279 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
fstab (END) 

```


**EXAMPLES OF DIFFERENT CD/DVD MOUNT PERMISSIONS**
```
**VIDEO TRANSFER DVD**

chad@chad-desktop:/media$ ls
cdrom  cdrom0  floppy  floppy0
chad@chad-desktop:/media$ cd cdrom0
bash: cd: cdrom0: Permission denied
chad@chad-desktop:/media$ ls -l
total 6
lrwxrwxrwx 1 root       root          6 2009-04-26 15:21 cdrom -> cdrom0
dr--r--r-- 3 4294967295 4294967295   88 2002-10-13 22:57 cdrom0
lrwxrwxrwx 1 root       root          7 2009-04-26 15:21 floppy -> floppy0
drwxr-xr-x 2 root       root       4096 2009-04-26 15:21 floppy0

**DATA DVD**

chad@chad-desktop:/media$ ls -l
total 10
lrwxrwxrwx 1 root root    6 2009-04-26 15:21 cdrom -> cdrom0
dr-xr-xr-x 1 root root 6144 2006-03-05 13:25 cdrom0
lrwxrwxrwx 1 root root    7 2009-04-26 15:21 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2009-04-26 15:21 floppy0
chad@chad-desktop:/media$ 

**COMMERCIAL DVD**

chad@chad-desktop:/media/cdrom0$ cd ..
chad@chad-desktop:/media$ ls -l
total 6
lrwxrwxrwx 1 root       root          6 2009-04-26 15:21 cdrom -> cdrom0
dr-xr-xr-x 3 4294967295 4294967295   88 2000-05-17 15:06 cdrom0
lrwxrwxrwx 1 root       root          7 2009-04-26 15:21 floppy -> floppy0
drwxr-xr-x 2 root       root       4096 2009-04-26 15:21 floppy0
chad@chad-desktop:/media$ 
```

What I really would like to do, is figure out how I can "fix" these DVDs, so I don't have to deal with this everytime I switch to a new OS.

Any help or ideas would be greatly appreciated.

Thanks

Chad

---

