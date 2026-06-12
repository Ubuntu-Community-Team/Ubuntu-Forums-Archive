---
title: "DVD Drive Does Not Mount On M1330 [Moved From Dell Support Forum]"
date: 2009-05-17
forum: Hardware
---

### Post by robog2 on 2009-05-17
This is on a Dell m1330 running Ubuntu 9.04 x64 (though I had a similar problem on 8.10).  

The dvd drive is not available in the places menu, but is visible in "Computer" in nautilus and has a mount location in "/media/" (both cdrom and cdrom0 are present).  When a cd is inserted, it does not mount, and the drive fails to recognize that one is present (though I hear it spin up).  I am positive that the drive itself works (and that the cds/dvds inserted work), but need help making it work in ubuntu.  

In 8.10, the drive would mount maybe one in ten times, but would not work correctly when it did; now it won't mount at all (after a clean install of 9.04).

I have thoroughly searched the forum, and have tried the solutions posted at [http://ubuntuforums.org/showthread.php?t=557405&highlight=m1330+dvd ]("http://ubuntuforums.org/showthread.php?t=557405&highlight=m1330+dvd")and the page to which it links to no avail.

Thanks,
Garrett

EDIT:

Here are the results of ```
ls -l /dev | grep cdrom
``` in case someone asks:

```

lrwxrwxrwx  1 root   root           3 2009-05-16 17:56 cdrom -> sr0
crw-rw----+ 1 root   cdrom    21,   1 2009-05-16 17:56 sg1
brw-rw----+ 1 root   cdrom    11,   0 2009-05-16 17:56 sr0

```

---

### Post by robog2 on 2009-05-18
Here's some more information; hopefully my problem will be more apparent with it:

When I try to mount (any) media manually:
```

sudo mount /media/cdrom0/ -o unhide
```
it returns:
```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

And when I do what it says:
```
dmesg | tail
```
I get this:
```
[  876.007501] sr: Sense Key : Hardware Error [current] 
[  876.007508] sr: Add. Sense: Tracking servo failure
[  876.013372] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 02 00 00 00 00 aa 00 0c 00
[  876.013395] sr: Sense Key : Hardware Error [current] 
[  876.013402] sr: Add. Sense: Tracking servo failure
[  876.013975] UDF-fs: No partition found (1)
[  876.053381] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[  876.053405] sr: Sense Key : Hardware Error [current] 
[  876.053413] sr: Add. Sense: Tracking servo failure
[  876.073386] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=32

```

Any help would be wonderful.  Thank you.

---

### Post by robog2 on 2009-05-19
Bump.  Added a bunch more information above.

---

### Post by robog2 on 2009-05-19
Bump.

---

### Post by robog2 on 2009-05-20
Bump.

---

