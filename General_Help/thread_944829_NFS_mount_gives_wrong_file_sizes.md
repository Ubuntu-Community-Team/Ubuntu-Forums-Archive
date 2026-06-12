---
title: "NFS mount gives wrong file sizes"
date: 2008-10-11
forum: General Help
---

### Post by CNLiberal on 2008-10-11
I have got a server with a 2TB RAID 5 mdadm array.  It's living in a new install 8.04.1 completely updated box.  It's serving out a folder through NFS and samba that have all my ISO movies and other TV shows on it.  On that server, I can see the file sizes of the movies just fine.  When I mount to the machine attached to my home theater, the sizes of the movies are wrong.  The sizes show as smaller, and this is causing NAV errors in xine etc.  I have no idea why this is happening.  As an FYI, this was working perfectly until last weekend when the OS drive in the server decided to take a dive.  So I replaced the drive, and put on a new MythBuntu 8.04.1 install.  I'm including the exports on the backend:

```
#/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)

#/storage               *(rw,async)
/storage/mythvideo      *(rw,async,insecure,no_subtree_check,no_root_squash,nohide)
/storage/pix            *(ro,async,no_root_squash,no_subtree_check)
/storage/music          *(ro,async,no_root_squash,no_subtree_check)
/storage/cover          *(ro,async,no_root_squash,no_subtree_check)
```

Here is the fstab for the frontend machine attached to the Home Theater.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c164040-1f13-4f3b-bb47-a57ae02bac46 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4318fa0b-4009-4445-b731-d23921bfaed0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
10.0.0.23:/storage/mythvideo    /var/lib/mythtv/videos          nfs4    defaults        1       2
10.0.0.23:/storage/pix          /var/lib/mythtv/pictures        nfs4    defaults        0       0
10.0.0.23:/storage/music        /var/lib/mythtv/music           nfs4    defaults        0       0
10.0.0.23:/storage/cover        /var/lib/mythtv/cover           nfs4    defaults        0       0

```

I am able to see the share through SMB on a windows laptop and the sizes are perfectly correct.  I'm installing the Windows NFS client so I can mount those directories.  I'll let you know if Windows sees it OK.

Jim

---

### Post by CNLiberal on 2008-10-11
I have confirmed that this is a problem with NFS on the backend server box.  What would be causing it to show incorrect file sizes?

---

