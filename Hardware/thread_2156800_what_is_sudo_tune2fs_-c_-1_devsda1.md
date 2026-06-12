---
title: "what is sudo tune2fs -c -1 /dev/sda1?"
date: 2013-06-23
forum: Hardware
---

### Post by aldrich199 on 2013-06-23
I don't know what "sudo tune2fs -c -1 /dev/sda1" use for???

---

### Post by MG&amp;TL on 2013-06-23
From *man tune2fs*:

```

DESCRIPTION
       tune2fs allows the  system  administrator  to  adjust  various  tunable
       filesystem  parameters  on  Linux ext2, ext3, or ext4 filesystems.  The
       current values of these options can be displayed by using the -l option
       to tune2fs(8) program, or by using the dumpe2fs(8) program.

       The  device  specifier can either be a filename (i.e., /dev/sda1), or a
       LABEL or UUID specifier: "LABEL=volume-name"  or  "UUID=uuid".   (i.e.,
       LABEL=home or UUID=e40486c6-84d5-4f2f-b99c-032281799c9d).

OPTIONS
       -c max-mount-counts
              Adjust  the  number of mounts after which the filesystem will be
              checked by e2fsck(8).  If max-mount-counts is 0 or -1, the  num&#8208;
              ber  of  times  the filesystem is mounted will be disregarded by
              e2fsck(8) and the kernel.

              Staggering the mount-counts at which  filesystems  are  forcibly
              checked  will  avoid  all  filesystems being checked at one time
              when using journaled filesystems.

              You should  strongly  consider  the  consequences  of  disabling
              mount-count-dependent   checking  entirely.   Bad  disk  drives,
              cables, memory, and kernel bugs could all corrupt  a  filesystem
              without  marking  the  filesystem dirty or in error.  If you are
              using journaling on your filesystem, your filesystem will  never
              be marked dirty, so it will not normally be checked.  A filesys&#8208;
              tem error detected by the kernel will still force an fsck on the
              next reboot, but it may already be too late to prevent data loss
              at that point.

              See also the -i option for time-dependent checking.


```

Here, */dev/sda1* is the filesystem to tune.

---

### Post by aldrich199 on 2013-06-23
Thanks very informative!!

---

